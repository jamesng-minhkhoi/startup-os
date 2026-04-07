# Hướng Dẫn Sử Dụng Startup OS — Dành Cho Team Petio

## Đây Là Gì?

Repo này là **bộ não chung** của team Petio. Tất cả thông tin về sản phẩm, khách hàng, thị trường, và kế hoạch đều được lưu ở đây. Claude tự động đọc và hiểu toàn bộ bối cảnh — không cần giải thích lại từ đầu mỗi lần chat.

> **Luôn bắt đầu ở [`DASHBOARD.md`](DASHBOARD.md)** — trang chủ của team. Cho bạn biết: trạng thái dự án, việc cần làm của từng người, quyết định đang chờ, và link đến tất cả tài liệu.

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

### `DASHBOARD.md` — Trang chủ (mở đầu tiên)

Mỗi khi mở repo, đọc file này trước:
- Trạng thái hiện tại + quyết định đang chờ
- Việc cần làm của **từng người** (James / Vy / Ngoc) theo priority
- Link đến tất cả tài liệu + document map theo chủ đề
- Blockers và milestones

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

File đặt tên `PENDING-REVIEW_[tên].md` = đang chờ ai đó duyệt. Xem DASHBOARD.md → bảng "Pending Decisions" để biết ai chờ gì.

---

## Quy Trình Làm Việc

### Hàng ngày

```
1. git pull                          ← lấy updates từ team
2. Mở DASHBOARD.md                   ← xem việc cần làm của mình
3. Làm việc (chạy workflow, viết content, research...)
4. Cập nhật context/ nếu có info mới
5. Nhờ Claude: "update DASHBOARD.md"  ← cập nhật trạng thái
6. git commit + push                 ← team thấy được
```

### Khi có quyết định cần team duyệt

1. Tạo file `PENDING-REVIEW_[tên].md` — ghi rõ: ai review, quyết định gì, deadline
2. Cập nhật DASHBOARD.md → bảng "Pending Decisions"
3. Thông báo người cần review (Slack / tin nhắn)
4. Sau khi duyệt: đổi tên bỏ `PENDING-REVIEW_` hoặc xóa nếu đã merge vào doc chính

### Khi hoàn thành sprint / milestone lớn

1. Nhờ Claude: "update sprint status" → `outputs/operations/sprint-status_[date].md`
2. Nhờ Claude: "update DASHBOARD.md" → action items, milestones, blockers
3. Cập nhật `context/` nếu có thay đổi lớn (features, market data, metrics)

### DASHBOARD.md vs Sprint Status — khác nhau thế nào?

| | DASHBOARD.md | Sprint Status |
|--|-------------|--------------|
| **Vai trò** | Bảng hành động — việc cần làm **bây giờ** | Lịch sử — việc đã **hoàn thành** |
| **Ai cập nhật** | Cả team, sau mỗi ngày làm việc | James, khi kết thúc sprint |
| **Chứa gì** | Action items theo người, pending decisions, blockers | Chi tiết công việc đã xong, quyết định đã đưa ra |
| **Xem khi nào** | Mỗi ngày | Khi cần review lại sprint trước |

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
- **Ops** — sprint planning, status updates, dashboard maintenance
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
2. Mở **[`DASHBOARD.md`](DASHBOARD.md)** — xem tổng quan dự án
3. Đọc 5 file trong `context/` để hiểu Petio đang ở đâu
4. Xem "Action Items" trong DASHBOARD.md → bắt đầu từ task HIGH
5. Thử gõ một prompt từ danh sách ở trên
6. Khi có info mới → cập nhật `context/` → commit + push
