# Petio Launch Scope — June 14, 2026

**Date:** 2026-05-02 · **For:** Ngoc, James

App reorganizes around **5 tabs**: Home · My Pet · Peti (center) · Scan · Memory.
No Reminders tab · No Stats tab · No Family screen. Settings + Notifications live in header icons.

---

## 1. What Ships

| Feature | Where it lives | Status | Owner |
|---|---|---|---|
| Onboarding (gamified pet creation, 9 steps) | First-run flow | Needs design | **Ngoc** |
| Pet profile (create + view, with allergens & conditions) | My Pet tab | Needs design | **Ngoc** |
| Home (empty + populated states) | Home tab | Design done in Figma | Ngoc → James |
| Peti AI chat | Peti tab (center) | Design done | Ngoc → James |
| Product scanner (barcode → Safe/Caution/Unsafe per pet) | Scan tab | Design done | Ngoc → James |
| Document upload + @mention in chat | Quick action / chat | Design done | Ngoc → James |
| Paywall (annual default, VND tier) | Onboarding + contextual | Light refresh needed | Ngoc light pass |
| Memory tab | Memory tab | 🟡 Flex — see §3 | Ngoc + James |
| Tiny Moments / Aww card (placeholder) | Home | "Coming soon" CTA only | James |
| Auth (Google / Apple / email) | Pre-onboarding | Visual refresh only | James |
| Settings hub | Header icon | Adapt existing | James |
| Notifications center | Header icon | Adapt existing | James |
| Scanner share card | Post-scan share button | Auto-generated from scan data | James |

---

## 2. What's Removed (Schema + UI Both Gone)

| Feature | What goes away | Knock-on effect |
|---|---|---|
| **Reminders** | Tab, CRUD screens, push schedules, schema | Vaccine date becomes a static profile field, no auto-reminders |
| **Statistics** | Tab, charts, weight tracking, all metrics | Peti can talk about weight but can't render the health chart widget |
| **Family Sync** | Invitations, member roles, shared pets | Single-user only · **Memories have no comments/reactions** |

---

## 3. Flex Scope — Memories

Decision deadline: **June 1, 2026** (2 weeks pre-launch).

- **If Ngoc lands design by Jun 1** → ship full Memory tab: create memory (photo + caption + feeling + tag pet), calendar view, gallery view, detail screen. No comments/reactions (Family is cut).
- **If not** → tab stays in nav with empty state "Coming soon — your pet's photo journal." Tiny Moments card on Home routes to the same toast.
