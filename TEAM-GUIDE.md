# Hướng Dẫn Sử Dụng Startup OS — Dành Cho Team Petio

## Đây Là Gì?

Repo này là **bộ não chung** của team Petio. Tất cả thông tin về sản phẩm, khách hàng, thị trường, và kế hoạch đều được lưu ở đây. Claude tự động đọc và hiểu toàn bộ bối cảnh — không cần giải thích lại từ đầu mỗi lần chat.

> **Luôn bắt đầu ở 2 nơi:**
> - **[`weekly/`](weekly/)** — file tuần hiện tại (ví dụ `weekly/2026-W22.md`). Bản tóm tắt tuần: TL;DR, số liệu, ship được gì, bets tuần tới.
> - **[`calendar.md`](calendar.md)** — tất cả deadline & ngày quan trọng. Email Friday 5pm sẽ tự tổng hợp 2 file này.

---

## Ai Dùng Tool Gì?

| Người | Tool | Ghi chú |
|-------|------|---------|
| **James** | Claude Code (CLI trong Terminal) | Code, deploy, system-level tasks, quản lý repo |
| **Vy** | Claude Desktop + CoWork | Marketing, customer research, content, partner management |
| **Ngoc** | Claude Desktop + CoWork | Design review, UX audit, microcopy, brand assets |

Tất cả đều kết nối vào cùng repo này. Output được lưu chung, context được chia sẻ.

---

## Cấu Trúc Repo

### `weekly/` — Note tuần (mở đầu tiên)

Mỗi tuần có 1 file riêng: `weekly/YYYY-WW.md` (ví dụ `2026-W22.md` cho tuần 22 năm 2026). Bot tự tạo từ `_template.md` mỗi sáng Thứ Sáu.

Mỗi file gồm:
- **TL;DR** — 2-3 câu tóm tắt tuần
- **Calendar** — tự động lấy từ `calendar.md` (overdue / tuần này / 30 ngày tới)
- **North Star** — chỉ số chính tuần đó
- **Numbers** — bảng metrics (downloads, signups, retention, etc.)
- **What shipped** — đã ship gì (app, design, marketing)
- **Voice of customer** — người dùng nói gì
- **Decisions made / pending** — quyết định đã/đang chờ
- **Bets next week** — mỗi owner 1 bet trọng yếu
- **Blockers** — bị kẹt ở đâu, ai unblock

### `calendar.md` — Mốc thời gian quan trọng

Single source of truth cho tất cả deadline:
- **Commitments** — sự kiện có ngày cụ thể (launch, decisions, milestones)
- **Recurring** — định kỳ (họp tuần Thứ Sáu 5pm, monthly metrics review)
- **Out of office** — ai đi vắng khi nào

Edit trực tiếp, hoặc nhờ Claude: *"add to calendar: June 7, brand guidelines locked, design, Ngoc"*.

### `context/` — Trí nhớ chung (5 file)

"Bộ nhớ" mà Claude và cả team đều đọc. **Cập nhật khi bạn biết thêm điều gì mới.**

| File | Nội dung |
|------|----------|
| `context/company.md` | Tầm nhìn, sứ mệnh, team, tài chính |
| `context/product.md` | Chi tiết sản phẩm, tính năng, roadmap |
| `context/market.md` | Quy mô thị trường, đối thủ, xu hướng |
| `context/customers.md` | Chân dung khách hàng, insight từ phỏng vấn |
| `context/metrics.md` | KPIs, OKRs, chỉ số quan trọng |

### `outputs/` — Deliverables (theo chức năng)

| Thư mục | Chứa gì |
|---------|---------|
| `outputs/strategy/` | Chiến lược, định vị, GTM, phân tích đối thủ |
| `outputs/marketing/` | Kế hoạch marketing, content, growth playbooks |
| `outputs/product/` | Discovery, specs, roadmap, experiments |
| `outputs/operations/` | Sprint status, process docs, runbooks |
| `outputs/finance/` | Financial models, runway, pricing |
| `outputs/hiring/` | JD, interview prep, org chart |

### File `PENDING-REVIEW_*.md` — Cần Duyệt

File đặt tên `PENDING-REVIEW_[tên].md` = đang chờ ai đó duyệt. Add vào bảng **Decisions pending** trong file tuần hiện tại (`weekly/YYYY-WW.md`) để team biết ai chờ gì.

---

## Quy Trình Làm Việc

### Hàng ngày

```
1. git pull                                ← lấy updates từ team
2. Mở weekly/YYYY-WW.md + calendar.md      ← xem tuần này có gì + deadline
3. Làm việc (chạy workflow, viết content, research...)
4. Cập nhật context/ nếu có info mới
5. Nhờ Claude: "update weekly file"        ← cập nhật số liệu, bets, blockers
6. git commit + push                       ← team thấy được
```

### Khi có quyết định cần team duyệt

1. Tạo file `PENDING-REVIEW_[tên].md` — ghi rõ: ai review, quyết định gì, deadline
2. Add vào `calendar.md` (category=decision) với ngày deadline
3. Add vào bảng **Decisions pending** trong file tuần hiện tại
4. Thông báo người cần review (Slack / tin nhắn)
5. Sau khi duyệt: đổi tên bỏ `PENDING-REVIEW_`, update status thành `done` trong calendar

### Khi hoàn thành sprint / milestone lớn

1. Nhờ Claude: "update sprint status" → `outputs/operations/sprint-status_[date].md`
2. Update file tuần hiện tại với: shipped items, decisions made, metrics
3. Cập nhật `context/` nếu có thay đổi lớn (features, market data, metrics)

### Weekly notes vs Calendar — khác nhau thế nào?

| | `weekly/YYYY-WW.md` | `calendar.md` |
|--|---------------------|----------------|
| **Vai trò** | Tóm tắt **tuần này** — narrative + metrics | Mốc thời gian xuyên suốt — deadline & milestone |
| **Tần suất** | 1 file/tuần, tạo Thứ Sáu | 1 file duy nhất, edit liên tục |
| **Chứa gì** | TL;DR, numbers, shipped, bets, blockers | Commitments có ngày, recurring, OOO |
| **Email Friday 5pm dùng** | Để hiển thị note tuần (link) | Để render section "Calendar" trong email |

### Quy tắc đặt tên file

- Tên mô tả + ngày: `vietnam-growth-playbook_2026-04-07.md`
- Cần duyệt: `PENDING-REVIEW_[tên].md`
- Đặt đúng thư mục theo chức năng (xem bảng outputs/ ở trên)

---

## Workflows — Claude Biết Làm Gì?

Mỗi workflow là một **quy trình nhiều bước** — bạn chỉ cần mô tả bạn muốn gì, Claude chạy toàn bộ và cho ra kết quả. Kết quả tự động lưu vào `outputs/`.

> **Lưu ý:** Các workflow có sẵn dưới dạng slash commands (ví dụ `/launch`, `/discover`) trong **Claude Code** (James dùng). **Vy & Ngoc trên Claude Desktop** không cần gõ `/command` — chỉ cần mô tả bằng ngôn ngữ tự nhiên, Claude sẽ tự chạy đúng quy trình. Bảng dưới đây là menu để biết Claude có thể làm gì.

### Nghiên Cứu & Chiến Lược

| Workflow | Mô tả | Ví dụ prompt |
|----------|-------|-------------|
| **Discover** | Nghiên cứu khách hàng → nhu cầu → giả định → thí nghiệm | "Chạy discovery cho tính năng AI meal planner cho chó" |
| **Validate** | Đánh giá ý tưởng → verdict: LÀM / SỬA / BỎ | "Validate: thêm đặt lịch bác sĩ thú y trong app" |
| **Compete** | So sánh đối thủ + tạo battlecard | "Phân tích PawHub — tính năng, giá, điểm yếu" |
| **Position** | Xác định khác biệt + messaging chính | "Chạy positioning workshop — messaging chưa rõ ràng" |
| **Canvas** | Tóm tắt mô hình kinh doanh trên 1 trang | "Tạo startup canvas cho Petio" |
| **Pitch** | Narrative + slide outline cho nhà đầu tư | "Xây pitch deck — pre-seed, 10-12 slides" |

### Marketing & Tăng Trưởng

| Workflow | Mô tả | Ví dụ prompt |
|----------|-------|-------------|
| **Launch** | Kế hoạch ra mắt: campaign, copy, checklist | "Plan launch food scanner — 1 triệu VND, 2 tuần" |
| **Growth** | Audit funnel AARRR → tìm bottleneck | "Growth audit — download nhiều nhưng churn ngày 3" |
| **GTM** | Go-to-market: ICP, kênh, pricing, 90-day plan | "GTM strategy cho Petio ở Việt Nam" |

### Vận Hành

| Workflow | Mô tả | Ví dụ prompt |
|----------|-------|-------------|
| **Sprint** | Prioritize backlog, chia task, viết spec | "Plan sprint 2 tuần — focus cải thiện onboarding" |
| **Review** | Đánh giá sức khỏe doanh nghiệp (EOS framework) | "Quarterly review — quý vừa rồi và quý tới?" |
| **Finance** | Doanh thu, chi phí, runway, pricing review | "Review tài chính — runway bao lâu?" |
| **Hire** | JD, interview prep, benchmarking lương | "Plan hire marketing intern — JD + câu hỏi" |

---

## Ai Làm Gì Với Claude?

### James (Engineering / Strategy) — Claude Code CLI

- **Code + deploy** — refactoring, features, bug fixes, CI/CD
- **Strategy** — competitor research, GTM, positioning, financial modeling
- **Ops** — sprint planning, weekly notes, calendar maintenance
- **Slash commands** — `/launch`, `/discover`, `/compete`, etc. (chỉ có trên CLI)

### Vy (Product / Marketing) — Claude Desktop + CoWork

- **Nghiên cứu khách hàng** — chuẩn bị phỏng vấn, phân tích feedback, tìm insight
- **Marketing** — viết copy, plan campaign, tạo content, email sequence
- **Partner management** — outreach, relationship tracking, brand guidelines
- **Metrics** — review số liệu hàng tuần, tìm bottleneck trong funnel

### Ngoc (Designer) — Claude Desktop + CoWork

- **Design review** — feedback về màn hình, flow, UI *(đính kèm screenshot)*
- **UX audit** — kiểm tra trải nghiệm người dùng
- **Brand assets** — partner kits, App Store screenshots, social templates
- **Microcopy** — text cho buttons, errors, empty states, CTAs

---

## Prompt Cheat Sheet — Dành Cho Vy & Ngoc

Nói chuyện bình thường bằng tiếng Anh hoặc tiếng Việt. Không cần gõ `/command` — chỉ cần mô tả bạn muốn gì.

### Khách Hàng & Thị Trường

> "Giúp mình chuẩn bị câu hỏi phỏng vấn cho pet parent có chó nhỏ, dùng mom-test"

> "Mình vừa phỏng vấn 5 khách hàng, đây là notes. Tổng hợp insight và cập nhật context/customers.md"

> "Tạo battlecard so sánh Petio vs PawHub"

### Marketing & Content

> "Lên content calendar cho TikTok tháng này — focus pet health tips"

> "Viết copy cho App Store listing — tập trung vào AI personalization"

> "Review landing page petiogo.com — chỗ nào cần cải thiện conversion?"

### Sprint & Phối Hợp

> "Tóm tắt những gì đã hoàn thành tuần này và việc còn lại cho tuần sau"

> "Cập nhật context/metrics.md — DAU tuần này là 150, tăng 20%"

> "Tạo checklist launch tính năng mới — trước launch, ngày launch, sau launch"

### Design & UX (Ngoc)

> "Review màn hình onboarding — feedback usability, hierarchy, consistency" *(đính kèm screenshot)*

> "Viết microcopy cho error messages và empty states trong app"

> "Tạo spec handoff cho developer từ design này"

---

## Bắt Đầu Lần Đầu

1. Nhờ James setup Claude Desktop cho bạn
2. Mở file tuần hiện tại trong **[`weekly/`](weekly/)** — xem tuần này có gì
3. Mở **[`calendar.md`](calendar.md)** — xem deadline sắp tới
4. Đọc 5 file trong `context/` để hiểu Petio đang ở đâu
5. Xem "Bets next week" trong weekly/ → bắt đầu từ bet của mình
6. Thử gõ một prompt từ danh sách ở trên
7. Khi có info mới → cập nhật `context/` → commit + push
