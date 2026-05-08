# Paywall — Copy Spec for Design

**Date:** 2026-05-08 · **For:** Ngoc · **From:** James + Vy · **Launch:** Jun 14, 2026

Pricing + copy for the paywall redesign. Visual direction is Ngoc's — this doc is the canonical source for every word and price that appears on screen.

> **Copy rule (non-negotiable):** Pet profiles are framed as **unlimited**. AI chat, scans, memories, and document storage say **"higher usage"** / **"more"** / **"expanded"**. **Never disclose specific Plus-tier numbers in user-facing copy** — internal anti-abuse caps exist but are an engineering concern, not a marketing one.

---

## 1. Pricing

| Tier | US / Global | Vietnam |
|---|---|---|
| Free | $0 | 0 ₫ |
| Plus Monthly | **$5.99 / month** | **79,000 VND / month** |
| Plus Annual ⭐ | **$47.99 / year** (~$4.00/mo) | **599,000 VND / year** (~50K VND/mo) |

**Annual savings vs monthly × 12:**
- US: $71.88 → $47.99 = **33% off**
- VN: 948,000 VND → 599,000 VND = **37% off**

**Display rules:**
- Use one badge globally: **"Save 33%"** (yellow)
- Annual is the default selected option everywhere — toggle defaults to `on`
- US users see USD only · VN users see VND only · never mix
- Pull price strings from RevenueCat `priceString` — no hardcoded fallbacks
- Show strikethrough comparison: $71.88 → $47.99 (US) · 948.000 ₫ → 599.000 ₫ (VN)

---

## 2. Surface A — Onboarding carousel

3 slides, after the social-proof step. Skippable from slide 1 (App Store requirement). Replaces today's 2-slide flow ("Family", "Memories") — Family Sync is cut.

| # | Image direction | Title (EN) | Title (VI) | Body (EN) | Body (VI) |
|---|---|---|---|---|---|
| 1 | Phone showing Peti chat answering "Is chocolate ok for Max?" with Max's profile bubble | **Peti knows your pet** | **Peti hiểu thú cưng của bạn** | Ask anything about your pet's food, behavior, or health — answers tailored to their breed, age, and allergies. | Hỏi bất cứ điều gì về ăn uống, hành vi hay sức khỏe — câu trả lời riêng cho giống, tuổi và dị ứng của bé. |
| 2 | Scanner viewfinder over a treat bag, "Unsafe for Max — contains chicken" pill | **Scan before they eat it** | **Quét trước khi cho ăn** | Point your camera at any pet food. Petio flags allergens specific to your pet — not generic warnings. | Hướng camera vào bất kỳ thức ăn nào. Petio cảnh báo dị ứng riêng cho bé — không phải lời khuyên chung. |
| 3 | Memory timeline tile with date scrubber | **Their whole story, in one place** | **Cả hành trình của bé, ở một nơi** | Photos, vet docs, and milestones — saved and searchable, so nothing important gets lost. | Ảnh, hồ sơ thú y và cột mốc — lưu và tìm được, để không bỏ lỡ điều gì quan trọng. |

**CTA on slides 1–2:** "See what's next" / "Xem tiếp"
**CTA on slide 3:** "Continue to Plus" / "Tiếp tục đến Plus"
**Skip:** top-right close ✕ → routes to home, no paywall.

---

## 3. Surface B — Main paywall

### Anatomy (top → bottom)

1. Hero illustration (placeholder today is `capa.svg` — needs real art; pet + Peti glow, warm not techy)
2. Headline (sells the *why*)
3. Plan toggle (Annual default ⭐ / Monthly)
4. Plan card — price, savings, what's included
5. Feature list — 5 bullets max
6. Primary CTA
7. Trust row — Cancel anytime · Auto-renews · Restore
8. Legal — Terms · Privacy
9. Close (✕) top-right, always visible

### Copy

**Headline (EN):** Petio Plus — more for every pet you care for
**Headline (VI):** Petio Plus — thêm cho mỗi bé bạn chăm

> Line 1 = "Petio Plus —" · Line 2 (accent, pink-300) = "more for every pet you care for"

**Sub-headline (EN):** Higher daily AI usage, more scans, unlimited pet profiles, and expanded storage for memories and documents.
**Sub-headline (VI):** Sử dụng AI nhiều hơn mỗi ngày, quét nhiều hơn, hồ sơ thú cưng không giới hạn, và mở rộng lưu trữ cho kỷ niệm và tài liệu.

### Plan card

**Annual selected (default):**
- Badge: **Save 33%** (yellow, top-right of plan card)
- Strikethrough: `$71.88` (US) · `948.000 ₫` (VN)
- Price: **`$47.99` / year** · **`599.000 ₫` / năm**
- Sub-line (US): `Just $4.00/month, billed annually`
- Sub-line (VN): `Chỉ ~50.000 ₫/tháng, thanh toán hàng năm`

**Monthly selected:**
- No badge
- Price: **`$5.99` / month** · **`79.000 ₫` / tháng**
- Sub-line (EN): `Billed monthly`
- Sub-line (VI): `Thanh toán hàng tháng`

### Feature bullets (5 max, AI-first order)

| # | EN | VI |
|---|---|---|
| 1 | Higher daily Peti AI usage — your pet's personal advisor | Dùng Peti AI nhiều hơn mỗi ngày — trợ lý riêng cho bé |
| 2 | Higher product scan usage — allergen warnings tailored to your pet | Quét sản phẩm nhiều hơn — cảnh báo dị ứng riêng cho bé |
| 3 | Unlimited pet profiles — care for every pet | Hồ sơ thú cưng không giới hạn — chăm cho mọi bé |
| 4 | Capture more memories · expanded document storage | Lưu thêm kỷ niệm · mở rộng dung lượng tài liệu |
| 5 | Early access to new AI features | Truy cập sớm các tính năng AI mới |

> ❌ **Do NOT include:** Family Sync (cut), Reminders (removed), Widgets (not shipping), advanced charts/Statistics (Stats tab removed).
>
> ❌ **Do NOT use the word "unlimited"** for AI chat, scans, memories, or documents. "Unlimited" applies *only* to pet profiles. Everything else: "higher", "more", "expanded".

### Buttons & links

| Element | EN | VI |
|---|---|---|
| Primary CTA (annual) | Get Plus — Save 33% | Nhận Plus — Tiết kiệm 33% |
| Primary CTA (monthly) | Get Plus Monthly | Nhận Plus Hàng Tháng |
| Trust row | Cancel anytime · Auto-renews · Restore purchases | Hủy bất kỳ lúc nào · Tự động gia hạn · Khôi phục giao dịch |
| Legal footer | Terms · Privacy | Điều khoản · Quyền riêng tư |

---

## 4. Surface C — Contextual paywall (bottom sheet)

Triggered when a free user hits a limit. ~78% screen height. Lead with the limit they hit. Same plan card as Surface B but compressed (no hero image).

| Trigger | Header (EN) | Header (VI) |
|---|---|---|
| Scan limit (after 3 free scans) | You've used your **3 free scans** today. Plus = higher daily usage. | Bạn đã dùng hết **3 lượt quét** miễn phí hôm nay. Plus = quét nhiều hơn mỗi ngày. |
| AI chat limit (after 5 free messages) | Peti's a bit chatty today — you've hit **5 free messages**. Plus = higher daily chat. | Peti hơi nhiều chuyện hôm nay — bạn đã dùng hết **5 tin nhắn** miễn phí. Plus = chat nhiều hơn mỗi ngày. |
| 2nd pet profile | Got another pet? Plus = **unlimited pet profiles**. | Có thêm bé nữa? Plus = **hồ sơ thú cưng không giới hạn**. |
| Memory limit (after 3 saved today) | You've saved **3 memories** today. Plus = higher daily capture. | Bạn đã lưu **3 kỷ niệm** hôm nay. Plus = lưu nhiều hơn mỗi ngày. |
| Document limit (after 5 docs) | Document storage is full on Free (**5 docs**). Plus = expanded storage. | Bộ nhớ tài liệu đã đầy ở gói Free (**5 tài liệu**). Plus = mở rộng dung lượng. |

**Headline below trigger:**
- EN: Keep going with **Petio Plus**
- VI: Tiếp tục với **Petio Plus**

**Plan card on this surface:** annual only (no toggle — keep it minimal). 3 features max, condensed:

| # | EN | VI |
|---|---|---|
| 1 | Higher Peti AI & scan usage | Dùng Peti AI & quét nhiều hơn |
| 2 | Unlimited pet profiles | Hồ sơ thú cưng không giới hạn |
| 3 | Capture more memories · expanded storage | Lưu thêm kỷ niệm · mở rộng dung lượng |

**Buttons:**

| Element | EN | VI |
|---|---|---|
| Primary CTA | Get Plus — Save 33% | Nhận Plus — Tiết kiệm 33% |
| Secondary | Maybe later | Để sau |

Secondary action closes the sheet, returns to free tier (limit remains, action stays blocked). Drag-down to dismiss = same as "Maybe later". Tap on backdrop = same. Grabber visible at top.
