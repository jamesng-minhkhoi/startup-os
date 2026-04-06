# Hướng Dẫn Sử Dụng Startup OS — Dành Cho Team Petio

## Đây Là Gì?

Repo này là **bộ não chung** của team Petio. Tất cả thông tin về sản phẩm, khách hàng, thị trường, và kế hoạch đều được lưu ở đây. Khi bạn mở Claude Desktop và kết nối vào thư mục này, Claude sẽ tự động đọc và hiểu toàn bộ bối cảnh của Petio — không cần giải thích lại từ đầu mỗi lần chat.

Mọi người trong team đều có thể:
- **Nghiên cứu** — phân tích khách hàng, đối thủ, thị trường
- **Lên kế hoạch** — chiến lược marketing, sprint, ra mắt tính năng
- **Phối hợp** — giao việc, ghi chú, cập nhật tiến độ
- **Tạo nội dung** — viết copy, email, bài social media

---

## Thông Tin Chung Của Petio Được Lưu Ở Đâu?

Thư mục `context/` chứa 5 file quan trọng — đây là "trí nhớ" chung của cả team:

| File | Nội dung |
|------|----------|
| `context/company.md` | Tầm nhìn, sứ mệnh, team, tài chính |
| `context/product.md` | Chi tiết sản phẩm, tính năng, roadmap |
| `context/market.md` | Quy mô thị trường, đối thủ, xu hướng |
| `context/customers.md` | Chân dung khách hàng, insight từ phỏng vấn |
| `context/metrics.md` | KPIs, OKRs, chỉ số quan trọng |

**Quan trọng:** Khi bạn biết thêm điều gì mới (ví dụ: phỏng vấn được khách hàng, phát hiện đối thủ mới, có số liệu mới), hãy cập nhật vào file tương ứng. Điều này giúp Claude cho ra kết quả tốt hơn cho tất cả mọi người.

---

## Các Workflow Có Sẵn — Claude Biết Làm Gì?

Startup OS có 13 workflow lớn. Mỗi workflow là một **quy trình nhiều bước** — thay vì bạn phải tự nghĩ từng bước, Claude sẽ chạy toàn bộ quy trình và cho ra kết quả hoàn chỉnh. Bạn chỉ cần mô tả bạn muốn gì.

### Khám Phá & Nghiên Cứu

**Discover (Khám phá sản phẩm)**
Chạy một chu trình nghiên cứu khách hàng hoàn chỉnh: phân tích khách hàng → tìm ra họ thực sự cần gì → liệt kê các giả định rủi ro → thiết kế thí nghiệm để kiểm chứng.

> "Chạy discovery cho tính năng AI meal planner cho chó — mình muốn hiểu pet parent thực sự cần gì"

**Validate (Kiểm chứng ý tưởng)**
Đánh giá một ý tưởng sản phẩm/tính năng mới. Claude sẽ phân tích qua nhiều góc độ (khách hàng, thị trường, mô hình kinh doanh) và cho verdict rõ ràng: **LÀM / SỬA LẠI / BỎ**.

> "Validate ý tưởng: thêm tính năng đặt lịch bác sĩ thú y trực tiếp trong app"

**Compete (Phân tích đối thủ)**
Phân tích sâu đối thủ cạnh tranh: so sánh tính năng, giá cả, điểm mạnh yếu, và tạo battlecard để team biết cách trả lời khi bị hỏi "sao không dùng app kia?"

> "Phân tích đối thủ PetDesk, Whistle, BarkBuddy — so sánh chi tiết và tạo battlecard"

### Chiến Lược & Định Vị

**Position (Định vị sản phẩm)**
Xác định Petio khác biệt ở đâu, nên nói gì với khách hàng, và nên đặt mình ở vị trí nào trên thị trường. Tạo ra messaging chính (headline, tagline, elevator pitch).

> "Chạy positioning workshop cho Petio — mình cảm thấy messaging hiện tại chưa rõ ràng"

**Canvas (Mô hình kinh doanh)**
Tạo hoặc cập nhật canvas chiến lược — một bản tóm tắt toàn bộ mô hình kinh doanh trên một trang, từ vấn đề khách hàng đến cách kiếm tiền.

> "Tạo startup canvas cho Petio — mình muốn nhìn lại toàn bộ mô hình"

**Pitch (Xây dựng pitch)**
Xây dựng câu chuyện pitch cho nhà đầu tư: narrative, slide outline, số liệu thị trường, và chiến lược thuyết phục.

> "Xây pitch deck cho Petio — pre-seed, mình cần outline 10-12 slides"

### Marketing & Ra Mắt

**Launch (Kế hoạch ra mắt)**
Lên kế hoạch ra mắt tính năng hoặc sản phẩm: chiến lược, campaign, viết copy, email, social media, và checklist ngày launch.

> "Plan launch cho food safety scanner — ngân sách 1 triệu, timeline 2 tuần"

**Growth (Kiểm tra tăng trưởng)**
Audit toàn bộ funnel tăng trưởng: acquisition → activation → retention → revenue → referral. Tìm ra **chỗ bị tắc nghẽn nhất** và đề xuất cách sửa.

> "Chạy growth audit — mình thấy nhiều người download nhưng ít ai dùng quá ngày 3"

**GTM (Chiến lược go-to-market)**
Xây dựng chiến lược đưa sản phẩm ra thị trường: xác định khách hàng mục tiêu, kênh marketing, pricing, và kế hoạch 90 ngày đầu.

> "Xây GTM strategy cho Petio ở thị trường Việt Nam — target pet parent gen Z ở TP.HCM"

### Vận Hành & Kế Hoạch

**Sprint (Lập kế hoạch sprint)**
Plan sprint phát triển: prioritize backlog, chia task, viết spec cho từng feature, xác định rủi ro và dependencies.

> "Plan sprint 2 tuần — team 3 người, focus vào cải thiện onboarding"

**Review (Đánh giá kinh doanh)**
Đánh giá tổng thể sức khỏe doanh nghiệp theo framework EOS: tầm nhìn, metrics, rocks (mục tiêu quý), team, tài chính, và vấn đề cần giải quyết.

> "Chạy quarterly review — quý vừa rồi mình đã làm gì, quý tới nên focus vào đâu?"

**Finance (Đánh giá tài chính)**
Review sức khỏe tài chính: doanh thu, chi phí, runway, pricing, và kế hoạch tài chính.

> "Review tài chính — mình đã chi bao nhiêu, còn runway bao lâu, pricing có hợp lý không?"

**Hire (Tuyển dụng)**
Lên kế hoạch tuyển dụng: xác định vị trí cần thiết, viết JD, thiết kế quy trình phỏng vấn, và benchmarking lương.

> "Plan hire cho vị trí marketing intern — viết JD và câu hỏi phỏng vấn"

---

## Lợi Ích Chính Khi Dùng Workflows

1. **Không cần nhớ quy trình** — Claude đã biết sẵn các bước cần làm, bạn chỉ cần nói bạn muốn gì
2. **Kết quả có chiều sâu** — mỗi workflow kết hợp 4-8 framework chuyên gia (ví dụ: launch = chiến lược + campaign + copywriting + CRO + checklist)
3. **Có chấm điểm** — Claude sẽ cho điểm 0-10 ở mỗi phần và gợi ý cách cải thiện lên 10/10
4. **Tất cả đều dựa trên context của Petio** — không phải lời khuyên chung chung, mà dựa trên thực tế sản phẩm, khách hàng, và số liệu của mình
5. **Kết quả được lưu lại** — mọi output đều được lưu vào repo, cả team đều có thể xem và build tiếp

---

## Cách Giao Tiếp Với Claude

Bạn chỉ cần nói chuyện bình thường bằng tiếng Anh hoặc tiếng Việt. Claude đã được hướng dẫn sẵn cách làm việc với Petio. Dưới đây là các loại prompt bạn có thể gõ:

### Nghiên Cứu Khách Hàng

Khi bạn muốn hiểu khách hàng tốt hơn, chuẩn bị phỏng vấn, hoặc phân tích dữ liệu từ khách hàng:

> "Giúp mình chuẩn bị câu hỏi phỏng vấn cho nhóm pet parent có chó nhỏ ở thành phố, dùng mom-test"

> "Phân tích feedback từ App Store reviews của Petio — tìm ra pain points chính"

> "Mình vừa phỏng vấn 5 khách hàng, đây là notes. Tổng hợp lại thành insight và cập nhật vào context/customers.md"

> "Phân tích xem khách hàng đang thuê Petio để làm gì (jobs-to-be-done)"

### Nghiên Cứu Đối Thủ & Thị Trường

Khi bạn muốn biết đối thủ đang làm gì, hoặc tìm cơ hội trên thị trường:

> "Phân tích đối thủ PetDesk, Whistle, và BarkBuddy — so sánh tính năng, giá, điểm mạnh yếu"

> "So sánh positioning của Petio với các app pet care khác — mình đang khác biệt ở đâu?"

> "Thị trường pet care app ở Việt Nam đang như nào? Cơ hội và rủi ro?"

> "Tạo battlecard so sánh Petio vs PetDesk để team biết cách trả lời khi bị hỏi"

### Lên Kế Hoạch Marketing & Ra Mắt

Khi bạn muốn plan chiến dịch, viết content, hoặc chuẩn bị launch:

> "Lên kế hoạch ra mắt tính năng food safety scanner — ngân sách 500k VND, timeline 2 tuần"

> "Viết copy cho App Store listing của Petio — tập trung vào AI personalization"

> "Tạo email sequence 5 ngày cho người dùng mới đăng ký"

> "Lên content calendar cho Instagram và TikTok tháng này — focus vào pet health tips"

> "Review landing page petiogo.com — chỗ nào cần cải thiện để tăng conversion?"

### Lên Kế Hoạch Sprint & Công Việc

Khi bạn muốn plan sprint, chia task, hoặc quyết định ưu tiên:

> "Plan sprint 2 tuần tới — team 3 người, deadline ra tính năng mới cuối tháng"

> "Có 10 feature ideas, giúp mình prioritize theo RICE framework"

> "Viết spec cho tính năng pet food scanner — problem, solution, acceptance criteria"

> "Review lại roadmap hiện tại — cái gì nên giữ, cái gì nên bỏ?"

### Ghi Chú & Cập Nhật Context

Khi bạn có thông tin mới và muốn lưu lại cho cả team:

> "Cập nhật context/customers.md — thêm insight: 70% pet parent lo lắng nhất về dinh dưỡng, không phải bệnh tật"

> "Cập nhật context/metrics.md — DAU tuần này là 150, tăng 20% so với tuần trước"

> "Cập nhật context/product.md — mình đã ship food scanner feature ngày 5/4"

> "Ghi chú vào context/market.md — PetDesk vừa raise Series B, $20M"

### Giao Việc & Phối Hợp

Khi bạn muốn ghi lại ai làm gì, hoặc tạo danh sách việc cần làm:

> "Tạo danh sách task cho sprint này và ghi rõ ai phụ trách — James: dev, Ngoc: design, Vy: marketing"

> "Tóm tắt những gì đã hoàn thành tuần này và việc còn lại cho tuần sau"

> "Tạo checklist cho launch tính năng mới — chia theo: trước launch, ngày launch, sau launch"

> "Viết status update cho team — gồm progress, blockers, và next steps"

### Thiết Kế & UX (Dành Cho Ngoc)

Khi bạn muốn review thiết kế hoặc cải thiện trải nghiệm người dùng:

> "Review màn hình onboarding này — feedback về usability, hierarchy, consistency" (đính kèm screenshot)

> "Audit UX flow từ lúc mở app đến lúc thêm pet đầu tiên"

> "Kiểm tra design có đúng Apple Human Interface Guidelines không?"

> "Viết microcopy cho error messages và empty states trong app"

> "Tạo spec handoff cho developer từ design này"

---

## Ai Nên Dùng Gì?

### Vy (Product / Marketing)

Bạn sẽ dùng nhiều nhất cho:
- **Nghiên cứu khách hàng** — chuẩn bị phỏng vấn, phân tích feedback, tìm insight
- **Marketing** — viết copy, plan campaign, tạo content, email sequence
- **Launch** — lên kế hoạch ra mắt tính năng, checklist, timeline
- **Metrics** — review số liệu hàng tuần, tìm bottleneck trong funnel

### Ngoc (Designer)

Bạn sẽ dùng nhiều nhất cho:
- **Design review** — nhận feedback chi tiết về màn hình, flow, UI
- **UX audit** — kiểm tra trải nghiệm người dùng toàn diện
- **iOS guidelines** — đảm bảo design đúng chuẩn Apple
- **Microcopy** — viết text cho buttons, errors, empty states, CTAs
- **Handoff** — tạo spec cho developer từ design

---

## Cách Phối Hợp Với Nhau

Repo này là nơi tập trung — mọi thứ đều ở đây:

1. **Trước khi làm việc** — pull repo để có thông tin mới nhất từ team
2. **Trong khi làm** — chạy workflow, cập nhật context, tạo output
3. **Sau khi làm** — commit và push để team thấy được

### Kết quả lưu ở đâu?

| Bạn muốn... | Lưu vào... |
|-------------|------------|
| Cập nhật thông tin khách hàng | `context/customers.md` |
| Lưu phân tích đối thủ | `outputs/strategy/` |
| Lưu nội dung marketing | `outputs/marketing/` |
| Lưu kế hoạch sprint | `outputs/product/` |
| Lưu báo cáo tài chính | `outputs/finance/` |

---

## Bắt Đầu Như Nào?

1. Nhờ James setup Claude Desktop + ClaudeCowork cho bạn
2. Đọc qua 5 file trong `context/` để hiểu Petio đang ở đâu
3. Thử gõ một prompt từ danh sách ở trên
4. Nếu bạn biết thông tin gì mà file context chưa có — cập nhật vào
5. Commit và push cho team
