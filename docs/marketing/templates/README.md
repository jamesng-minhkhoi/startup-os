# AI Content Templates

Copy-paste prompts that generate on-brand Petio content. Each one tells the AI to read the context files first, then produce content following Petio's brand rules — so output is personalized, not generic.

## How to use
1. Open Claude in this repo (or paste into any Claude chat with the context files attached).
2. Copy the **Prompt** block from the template you want.
3. Fill the `<…>` placeholders (brand, breed, topic, etc.).
4. Generate → review against the **Checklist** → log the published piece in `../content/content-tracker.md`.

## Templates

| Template | Use for | Market |
|----------|---------|--------|
| `tiktok-scan-demo.md` | "Is This Safe?" / "Boss đang ăn gì?" scan videos | VN + US |
| `fb-group-value-post.md` | Helpful Facebook group posts (trust-first) | VN |
| `ig-carousel.md` | Educational IG carousels | VN |
| `threads-vn-generator-prompt.md` | Community-adaptive Threads posts (anti-AI-detect, brand <5%) | VN |
| `threads-vn-pet-style-guide.md` | Voice reference for Threads VN pet niche (pairs with the generator) | VN |
| `reddit-helpful-comment.md` | Value-first Reddit comments/posts | US |
| `blog-post-seo.md` | Long-form SEO articles | VN + US |
| `ab-test-brief.md` | Design an A/B test before running it | both |

## Brand rules every template enforces
- Read `context/product.md` + `context/customers.md` + `context/market.md` first.
- **Value-first, app-second** — especially during the iOS-only window.
- **Native Vietnamese** for VN (never translated); plain, warm, founder voice.
- **Hero CTA = free Food Checker** (`petiogo.com/vi/tools/kiem-tra-thuc-an`) while Play Store is pending; iOS App Store only when asked; Android → waitlist.
- **No medical/diagnosis claims** — "kiểm tra thành phần / ingredient check", never "chẩn đoán / diagnose".
- Use **real, popular brands** (VN: Pedigree, Ganador, SmartHeart, Me-O, Royal Canin · US: Milk-Bone, Beggin' Strips, Blue Buffalo).
