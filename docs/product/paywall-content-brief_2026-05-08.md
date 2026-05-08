# Paywall — Content Brief for Design

**Date:** 2026-05-08 · **For:** Ngoc · **From:** James + Vy · **Status:** Light refresh per launch scope (Jun 14, 2026 launch)

This brief gives you the **content + copy + structure** to redesign the paywall. Visual direction is yours. Pricing, feature list, and copy here are the canonical source — the current app strings are out of date and must be replaced.

---

## 1. Why we're touching the paywall

Current paywall (in app today) has three problems:

1. **Wrong copy** — lists Family Sync, Reminders, and Widgets as Plus features. All three were cut or removed. Lists "Save 30%" when actual annual savings are **33%**.
2. **Wrong pricing on screen** — fallback strings hardcode the old `$3.99` / `$34.99`. Real launch prices are `$5.99` / `$47.99` (US) and `79,000 VND` / `599,000 VND` (Vietnam).
3. **Wrong story** — paywall sells "unlimited limits" instead of the AI value. Our positioning is **"Your pet's personal AI"** — the paywall should reinforce that, not list quotas.

Goal of redesign: make annual default obvious, make the AI value the headline, work in VND without USD bleeding through.

---

## 2. Single source of truth — Pricing & limits

> **⚠️ Limit change (2026-05-08):** AI chat and documents are no longer unlimited on Plus — they consume real cost (Gemini API + Supabase storage). New caps: **50 AI msgs/day**, **50 docs total**. Pet profiles bumped to **10** to compensate. Scans and memories stay unlimited.

| Tier | US / Global | Vietnam | Limits |
|---|---|---|---|
| Free | $0 | 0 ₫ | 5 AI msgs/day · 3 scans/day · 1 pet · 3 memories/day · 5 docs |
| Plus Monthly | **$5.99 / month** | **79,000 VND / month** | See Plus row below |
| Plus Annual ⭐ | **$47.99 / year** (~$4.00/mo) | **599,000 VND / year** (~50K VND/mo) | See Plus row below |

**Plus tier limits (new):**
- **50 AI messages / day** (10× Free) — capped to control Gemini API cost
- **Unlimited product scans** — barcode lookup, low marginal cost
- **Up to 10 pet profiles** (bumped from 5) — covers multi-pet families
- **Unlimited memories** — photo capture, low marginal cost
- **50 documents total** (was unlimited) — storage cap

**Annual savings vs monthly × 12:**
- US: $71.88 → $47.99 = **33% off** (~$24/yr saved)
- VN: 948,000 VND → 599,000 VND = **37% off** (~349K VND/yr saved)

> Use **"Save 33%"** badge globally for now (one badge, not two — keeps build simple). VND localization on price string only.

**Annual must be the default selected option** at all times — that's the entire point of the redesign. Monthly is a secondary toggle.

---

## 3. Surfaces to design

The paywall lives in **three places**. They share visual DNA but have different jobs.

### Surface A — Onboarding upsell (after social-proof step)
**Route:** `/(protected)/unlock-full-experience` → `/paywall`
**Goal:** Plant the seed. User just finished setting up their pet. Optional. Skip is allowed.
**Format today:** 2-slide carousel ("Family", "Memories") then routes to paywall. Family content is now wrong — Family Sync is cut.

### Surface B — Main paywall (purchase screen)
**Route:** `/paywall`
**Goal:** Convert. Annual default. Single CTA. Restore link. Cancel link.

### Surface C — Contextual paywall (in-line, when user hits a limit)
**Trigger:** 4th scan today, 6th AI msg today, 2nd pet, 4th memory today, 6th doc.
**Format:** Bottom sheet (Vy's call — simpler than full screen, less interruption).
**Goal:** Convert at moment of intent. Lead copy with **the specific limit they hit**.

---

## 4. Surface A — Onboarding carousel (replaces current 2-slide flow)

Drop the "Family" slide entirely. Replace with **3 slides built around the AI-first pivot**:

| # | Image direction | Title (EN) | Title (VI) | Body (EN) | Body (VI) |
|---|---|---|---|---|---|
| 1 | Phone showing Peti chat answering "Is chocolate ok for Max?" with Max's profile bubble | **Peti knows your pet** | **Peti hiểu thú cưng của bạn** | Ask anything about your pet's food, behavior, or health — answers tailored to their breed, age, and allergies. | Hỏi bất cứ điều gì về ăn uống, hành vi hay sức khỏe — câu trả lời riêng cho giống, tuổi và dị ứng của bé. |
| 2 | Scanner viewfinder over a treat bag, "Unsafe for Max — contains chicken" pill | **Scan before they eat it** | **Quét trước khi cho ăn** | Point your camera at any pet food. Petio flags allergens specific to your pet — not generic warnings. | Hướng camera vào bất kỳ thức ăn nào. Petio cảnh báo dị ứng riêng cho bé — không phải lời khuyên chung. |
| 3 | Memory timeline tile with date scrubber | **Their whole story, in one place** | **Cả hành trình của bé, ở một nơi** | Photos, vet docs, and milestones — saved and searchable, so nothing important gets lost. | Ảnh, hồ sơ thú y và cột mốc — lưu và tìm được, để không bỏ lỡ điều gì quan trọng. |

**CTA on every slide:** "See what's next" / "Xem tiếp"
**Skip:** top-right close → routes to home (no paywall). Skip must be visible — required for App Store compliance on optional upsells.

---

## 5. Surface B — Main paywall

### Anatomy (top → bottom)

1. **Hero illustration** (placeholder today is `capa.svg` — needs real art)
   - Suggested concept: pet + phone + Peti glow. Warm, not techy.
2. **Headline** — sells the *why*, not the *what*.
3. **Plan toggle** (Annual default ⭐ / Monthly)
4. **Plan card** — price, savings, what's included
5. **Feature list** — 5 bullets max, AI-first order
6. **Primary CTA** — "Get Plus Annual"
7. **Trust row** — Cancel anytime · Restore · Terms · Privacy
8. **Close (X)** — top-right, always visible

### Copy

**Headline (EN):** More Peti, more pets, more memories
**Headline (VI):** Thêm Peti, thêm thú cưng, thêm kỷ niệm

**Sub-headline (EN):** 10× more daily AI answers, scans for every product you check, room for up to 10 pets, and unlimited memory capture.
**Sub-headline (VI):** Tăng 10× câu trả lời AI mỗi ngày, quét mọi sản phẩm, tối đa 10 hồ sơ thú cưng, và lưu kỷ niệm không giới hạn.

### Plan card content

**Annual selected (default):**
- Badge: **Save 33%** (yellow, top-right of plan card)
- Strikethrough: `$71.88` / `948,000 ₫`
- Price: **`$47.99` / year** · **`599,000 ₫` / năm**
- Sub-line: `Just $4.00/month, billed annually` / `Chỉ $4.00/tháng, thanh toán hàng năm`
  - VN sub-line: `Chỉ ~50,000 ₫/tháng, thanh toán hàng năm`

**Monthly selected:**
- No badge
- Price: **`$5.99` / month** · **`79,000 ₫` / tháng**
- Sub-line: `Billed monthly` / `Thanh toán hàng tháng`

### Feature bullets (replace current 4 — these reflect what actually ships June 14)

| # | EN | VI |
|---|---|---|
| 1 | 10× more Peti AI chat — 50 personalized answers per day | Peti AI nhiều hơn 10× — 50 câu trả lời cá nhân hóa mỗi ngày |
| 2 | Unlimited product scans — allergen warnings tailored to your pet | Quét sản phẩm không giới hạn — cảnh báo dị ứng riêng cho bé |
| 3 | Up to 10 pet profiles — care for the whole crew | Tối đa 10 hồ sơ thú cưng — chăm cả đại gia đình |
| 4 | Unlimited memory capture · up to 50 documents | Lưu kỷ niệm không giới hạn · tối đa 50 tài liệu |
| 5 | Early access to new AI features | Truy cập sớm các tính năng AI mới |

> ❌ Remove from current build: Family sync (cut), Reminders (removed), Widgets (not shipping), generic "advanced health insights" (no charts at launch — Stats tab is removed). Also: do **not** use the word "unlimited" for AI chat or documents — those are now capped.

### Buttons & links

| Element | EN | VI |
|---|---|---|
| Primary CTA (annual) | Get Plus — Save 33% | Nhận Plus — Tiết kiệm 33% |
| Primary CTA (monthly) | Get Plus Monthly | Nhận Plus Hàng Tháng |
| Trust line | Cancel anytime · Auto-renews · Restore | Hủy bất kỳ lúc nào · Tự động gia hạn · Khôi phục |
| Legal footer | Terms · Privacy | Điều khoản · Quyền riêng tư |

---

## 6. Surface C — Contextual paywall (bottom sheet)

Triggered when a free user hits a limit. Same plan card as Surface B, but with a **limit-specific header** so the offer feels relevant, not generic.

| Trigger | Header (EN) | Header (VI) |
|---|---|---|
| 4th scan today | You've used your 3 free scans today. Plus = unlimited scans. | Bạn đã dùng hết 3 lượt quét miễn phí hôm nay. Plus = quét không giới hạn. |
| 6th AI msg today | Peti's a bit chatty today — you've hit 5 free messages. Plus = 10× more (50/day). | Peti hơi nhiều chuyện hôm nay — bạn đã dùng hết 5 tin nhắn miễn phí. Plus = 10× nhiều hơn (50/ngày). |
| 2nd pet profile | Got another pet? Plus lets you care for up to 10. | Có thêm bé nữa? Plus cho phép chăm tối đa 10 bé. |
| 4th memory today | You've saved 3 memories today. Plus = unlimited capture. | Bạn đã lưu 3 kỷ niệm hôm nay. Plus = lưu không giới hạn. |
| 6th document | Document storage is full on Free (5). Plus stores up to 50. | Bộ nhớ tài liệu đã đầy ở gói Free (5). Plus lưu tối đa 50 tài liệu. |

Below the header, show the **same Annual-default plan card** as Surface B but compressed (no hero image; sheet height ~70% of screen).

Secondary action: `Maybe later` / `Để sau` — closes the sheet, returns to free tier.

---

## 7. States Ngoc needs to spec

For each surface, please cover:

- **Default** — annual selected, prices loaded
- **Loading** — fetching offerings from RevenueCat (skeleton on plan card)
- **Purchase in progress** — CTA shows spinner, disabled
- **Purchase success** — toast + auto-dismiss to previous screen
- **Restore success / no sub found / error** — alert dialogs (copy already in i18n, fine as-is)
- **Offline / offerings failed to load** — fallback message: "Can't load plans. Check connection." / "Không tải được gói. Kiểm tra kết nối."

---

## 8. Localization rules

- VN users see **VND only** — never USD anywhere on the screen.
- US/Global users see **USD only**.
- All price strings come from RevenueCat `priceString` — designs should use that as the source, not hardcoded numbers (no more `$34.99` fallbacks).
- VI translations exist for everything — Ngoc, please review the VI copy in §4–6 with Vy before finalizing (we're not native).

---

## 9. Open questions for Ngoc + Vy before design starts

| # | Question | Owner |
|---|---|---|
| 1 | Do we add a **7-day free trial** at launch? Affects CTA copy ("Start free trial" vs "Get Plus") and plan card layout. | Vy + James |
| 2 | Contextual paywall — bottom sheet (planned) or full screen? Spec says sheet; confirm before design. | Ngoc |
| 3 | Hero illustration: commission a new one or use Peti mascot we already have? | Ngoc |
| 4 | Should the onboarding carousel be skippable on every slide, or only after slide 3? (App Store wants it skippable from slide 1.) | James |

---

## 10. Handoff checklist

When Ngoc's done, we need from Figma:
- [ ] Surface A (3 slides) — light + dark
- [ ] Surface B (annual + monthly states) — light + dark, EN + VI
- [ ] Surface C (5 trigger variants) — at minimum the scan + chat ones
- [ ] All loading / error / success states
- [ ] Updated hero illustration (or confirmation we reuse existing asset)
- [ ] Spec for "Save 33%" badge style (reusable component)

After Figma signoff, James updates `screens/paywall/PaywallScreen.tsx`, `screens/paywall/UnlockFullExperienceScreen.tsx`, and the `paywall` + `unlockExperience` keys in `locales/{en,vi}/translation.json` to match.

**Pre-launch dependency (not Ngoc's):** RevenueCat dashboard pricing must be updated from `$3.99/$34.99` to `$5.99/$47.99` and the VND tier (`79K/599K`) added. Owner: James. Blocker for VN marketing.
