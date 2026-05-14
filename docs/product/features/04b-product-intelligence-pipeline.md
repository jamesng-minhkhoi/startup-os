# Product Intelligence Pipeline
**Last updated**: 2026-05-14 | **Status**: Planned

> This spec supersedes the simplified database integration note in `04-product-scanner.md`. The scanner does not do a single barcode lookup — it runs a multi-tier product intelligence pipeline with cascading fallbacks, crowdsourced corrections, and a unified data schema.

---

## What This Is (Plain English)

The Product Scanner needs to identify any pet food or treat product accurately and instantly, then run it against the pet's health profile. The problem: no single source covers all pet products. Open Food Facts has 4M+ human food items but thin pet coverage. Many products — private-label brands, regional sellers, and anything not in a major database — have no barcode entry anywhere.

The answer is a multi-tier pipeline: try the best sources first, fall back gracefully, and let users fill the gaps. Over time, Petio's own catalog becomes a proprietary moat that no competitor can replicate.

---

## Tiered Lookup Cascade

```
Barcode scanned
     │
     ▼
┌─────────────────────────────┐
│ T1: Open Pet Food Facts     │ ◄── PRIMARY (highest pet coverage, free)
│ T1: Open Food Facts        │ ◄── SECONDARY (supplements, human food overlap)
│ T1: GS1 + USDA            │ ◄── TERTIARY (manufacturer + nutrient data)
└─────────────────────────────┘
     │ matched
     │ no match
     ▼
┌─────────────────────────────┐
│ T2: LLM Inference          │ ◄── Identifies product from barcode via Gemini
│                             │     Must provide source attribution in response
└─────────────────────────────┘
     │ identified but
     │ no ingredient data
     ▼
┌─────────────────────────────┐
│ T3: OCR Fallback           │ ◄── User scans front label / ingredients panel
│                             │     LLM extracts structured fields from image
└─────────────────────────────┘
     │ OCR fails or
     │ barcode missing
     ▼
┌─────────────────────────────┐
│ T4: Image Embedding Match  │ ◄── Match packaging photo against internal catalog
│                             │     Builds proprietary coverage over time
└─────────────────────────────┘
     │ still no match
     ▼
┌─────────────────────────────┐
│ T5: Crowdsourced Catalog   │ ◄── User submits product + image
│                             │     Queued for verification workflow
└─────────────────────────────┘
     │ still nothing
     ▼
"Product not found — help us build our database"
[Submit Product] button
```

---

## Data Sources

### T1 Sources (Structured Database Lookup)

**Open Pet Food Facts** — PRIMARY
- 50-60% hit rate on major pet food brands (Hill's, Purina, Royal Canin, Blue Buffalo, Orijen, Acana, Wellness, etc.)
- Free, open license (ODbL), updated by community
- API: `https://world.openpetfoodfacts.org/api/v2/product/{barcode}`
- Returns: product name, brand, ingredients, allergens, nutrition facts, images
- Coverage gaps: private-label brands (Amazon Basics Pet, Trader Joe's Pet, Costco Kirkland), regional brands, products sold only in specialty stores

**Open Food Facts** — SECONDARY
- Covers supplements, human food that overlaps with pet use (peanut butter, pumpkin, coconut oil)
- API: `https://world.openfoodfacts.org/api/v2/product/{barcode}`
- Useful as fallback when OPFF returns no result

**GS1 / GTIN Registry**
- Identifies brand and manufacturer from GTIN prefix
- Free lookup: `https://www.gs1.org/company-colonization-data`
- Does NOT return ingredients — only brand identity
- Use case: when barcode is unknown, at least identify the brand to pass context to LLM

**USDA FoodData Central**
- Covers ingredients and nutrients for raw/packaged ingredients
- API: `https://api.nal.usda.gov/fdc/v1`
- Useful for ingredient-level safety cross-reference (e.g., "is xylitol in this?")

### T2: LLM Inference

- Triggered when T1 sources return no result
- Input: barcode value + pet profiles
- Output: product name, brand, ingredients, safety assessment
- **Rule: LLM must cite source or state "no verifiable source found"** — no fabricating ingredient lists without attribution
- If LLM cannot identify the product: fall through to T3 (OCR)

### T3: OCR Fallback

When barcode is missing, damaged, or unrecognised:

1. Prompt user: "Scan the ingredients label on the package"
2. Camera captures: front label + ingredients panel + nutrition facts + warnings + brand name
3. OCR extracts text from image
4. LLM parses OCR output → maps to unified Product schema
5. Stored as `verification_status: "ai_extracted"` for human review

**UX requirements:**
- Show real-time camera preview with target zone indicator
- Guide user to position ingredients panel (not barcode) in frame
- Provide example screenshot of what "good" looks like
- Minimum 3 successful OCR captures to confirm the flow works

### T4: Image Embedding Match

When T1-T3 all fail:
- User takes a photo of the product packaging
- Embedding model (e.g., CLIP or equivalent) encodes image
- Cosine similarity against internal product catalog embeddings
- If top match score > threshold (e.g., 0.85): return matched product
- If match score < threshold: fall through to T5

**Cold start:** Seed internal catalog with user-submitted images from the crowdsourced loop. Every verified submission becomes a catalog entry.

### T5: Crowdsourced Catalog

Every "product not found" is an opportunity:
- User submits: packaging photo + product name + brand (optional)
- Stored in Supabase pending queue
- Verified via: OCR extraction → admin review → brand_verified if brand confirms
- Verified users can mark products as "correct" directly (raises confidence_score)
- Gamify: contributor badge after 3 verified submissions

---

## Safety Score: How It's Calculated

> The score is **deterministic**. It must be disclosed to the user — they must be able to see exactly how it was calculated. The LLM does not generate the score. It summarizes information from the data source.

### Score Inputs (deterministic, user-disclosed)

| Input | Weight | Source |
|-------|--------|--------|
| Known allergen in ingredients list | 100 (immediate fail) | Pet profile allergies + ingredient scan |
| Species-unsafe ingredient (e.g., chocolate for dogs) | 100 (immediate fail) | Safety rule engine |
| Health condition contraindication | 100 (immediate fail) | Pet profile conditions |
| Ingredient of concern (by-product, artificial additive) | 30 points off | OPFF/AIFF ingredient taxonomy |
| Nutritional completeness | 10 points off | OPFF nutrition grade |
| Age-inappropriate (e.g., puppy formula for senior dog) | 15 points off | Life stage + species data |

### Score Output

```
Score = 100 - deductions
100 = SAFE (green)
70-99 = CAUTION (yellow)
0-69 = UNSAFE (red)
```

### Display to User

Every result card must show:
- The score (e.g., "Score: 78 / 100 — CAUTION")
- The deduction breakdown: "−30 pts: BHA preservative found in ingredients"
- The source(s) used: "Source: Open Pet Food Facts, verified 2025-03-12"
- If no verified source: "Source: Community data — help verify this product"

The LLM's role is **summary only**: it explains what the flagged ingredient is and why it matters for this pet's specific situation. It does not generate the score.

---

## Unified Product Data Schema

```typescript
Product {
  id: uuid                    // internal identifier
  gtin?: string              // Global Trade Item Number
  barcode?: string           // UPC-A / EAN-13 value
  name: string              // product display name
  brand?: string             // brand name
  manufacturer?: string      // manufacturer name
  category: "pet_food" | "pet_treat" | "pet_item" | "human_food" | "supplement" | "unknown"
  species?: ("dog" | "cat" | "bird" | "small_pet")[]
  life_stage?: ("puppy" | "kitten" | "adult" | "senior" | "all_life_stages")[]
  ingredients?: string[]
  allergens?: string[]      // extracted from ingredients list
  guaranteed_analysis?: Record<string, string>  // crude_protein, crude_fat, fiber, moisture
  calorie_content?: number   // kcal/cup or kcal/kg
  feeding_guidelines?: string
  warnings?: string[]
  images?: string[]         // packaging photos
  data_sources: SourceRecord[]
  confidence_score: number   // 0-1, weighted across sources
  verification_status: "unverified" | "ai_extracted" | "user_confirmed" | "admin_verified" | "brand_verified"
  last_verified_at?: timestamp
  created_at: timestamp
  updated_at: timestamp
}

SourceRecord {
  source: "open_pet_food_facts" | "open_food_facts" | "usda" | "gs1" | "retailer" | "ocr" | "llm" | "user" | "brand"
  source_id?: string
  source_url?: string
  raw_data?: jsonb           // preserved original data for audit
  confidence: number         // 0-1, source reliability score
  fetched_at: timestamp
  verified_by?: uuid        // user or admin who confirmed this entry
}
```

---

## Build Order

| Phase | What's Built | Target |
|-------|-------------|--------|
| **Phase 1** | T1: OPFF + OFF API integration as primary lookup | Scanner accuracy at launch |
| **Phase 2** | Deterministic safety score engine + disclosure UI | Replace LLM-generated scores |
| **Phase 3** | T3: OCR fallback pipeline | Cover missing barcodes |
| **Phase 4** | T5: User product submission + verification workflow | Compound data moat from Day 1 |
| **Phase 5** | T4: Image embedding catalog (CLIP or equivalent) | Private label / regional coverage |
| **Phase 6** | GS1 brand lookup + USDA ingredient cross-reference | Brand ID + ingredient safety check |
| **Phase 7** | Manufacturer self-serve portal + GS1 Digital Link | Long-term coverage + data quality |

---

## Open Questions

| Question | Status |
|----------|--------|
| GS1 Digital Link support for newer barcodes? | Open — engineer to evaluate feasibility for Phase 6 |
| Threshold for image embedding match confidence? | Default 0.85 — tune after Phase 5 user testing |
| Admin verification workflow — who reviews crowdsourced submissions? | James (founder) initially; consider community moderators post-launch |
| Target catalog size at launch? | 50 pre-loaded verified products from OPFF (top brands) |