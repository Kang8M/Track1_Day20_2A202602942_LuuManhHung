# 02 — Action Nature Card + kết luận cadence

> Phase 2 · 15 phút · [← Mục lục](../metrics-pack.md) · [← 01](../01/README.md)

## Nguồn dữ liệu

Các con số ở mục này lấy từ **một cuộc phỏng vấn nhân viên Pháp chế đang làm việc thật (n = 1)**. Chỉ một người nên chưa đại diện cho cả ngành. Số liệu là mốc khởi điểm, cần đo lại bằng dữ liệu `contract_uploaded` → `contract_review_published` khi sản phẩm chạy.

| Câu hỏi | Câu trả lời của người được phỏng vấn | Dùng cho trường |
| --- | --- | --- |
| Khối lượng mỗi tuần? | Trung bình **1–3 hợp đồng/tuần** | Cadence |
| Thời gian mỗi hợp đồng? | **1–2 giờ**, tuỳ độ dài và độ phức tạp | Effort |
| Hợp đồng đến từ đâu? | **Kênh nội bộ**, khi công ty có dự án mới | Trigger |
| Có tuần nào trống không? | Trong 1 tháng có **ít nhất 1 tuần** không có hợp đồng cần soát | Cadence, Retention |
| Mẫu HĐMB đổi khi nào? | Thường khi **luật thay đổi** hoặc có **dự án mới** (người trả lời nói không nắm rõ) | Repeat condition |
| Khi nào cần Trưởng phòng duyệt lại? | Khi **khó tự quyết**, khi đang **lưỡng lự giữa quyền lợi các bên**, hoặc liên quan **quy định pháp luật** | Dependency |

## 1. Action Nature Card

| Thành phần | Câu trả lời |
| --- | --- |
| **Actor** | Cá nhân Nhân viên Pháp chế (`reviewer_id`). Phòng Pháp chế chịu trách nhiệm pháp lý, nhưng hành vi do một người thực hiện và ký tên → giữ actor ở cấp cá nhân |
| **Intent** | Cần phát hành/duyệt **một hợp đồng cụ thể** mà không gánh rủi ro sót điều khoản |
| **Trigger** | **Nguồn bên ngoài người dùng** — hợp đồng đến qua **kênh nội bộ khi công ty có dự án mới**. Không phải user tự nhiên mở app. Người gửi cụ thể (Sale, CĐT hay bộ phận khác) chưa xác minh |
| **Effort** | Trung bình: **1–2 giờ/hợp đồng** (phỏng vấn n=1). Đọc hợp đồng, đối chiếu với quy định pháp luật, viết đề xuất sửa. Cần bản hợp đồng, mẫu chuẩn nội bộ, tiền lệ đã duyệt |
| **Value timing** | **Ngay** khi xuất bản kết luận (biết hợp đồng đã sạch rủi ro trọng yếu) · **tích luỹ** (thư viện tiền lệ càng dày thì soát càng nhanh) · một phần **trễ rất xa** (giá trị thật chỉ xác nhận khi không phát sinh tranh chấp sau bàn giao — quá trễ để làm metric) |
| **State** | Hợp đồng + tập phát hiện + quyết định & lý do từng phát hiện + bản redline + `reviewer_id` + timestamp → kết tinh thành **thư viện tiền lệ nội bộ** (đã có trong sản phẩm) và bộ mẫu điều khoản đã duyệt. Đây là investment của loop |
| **Dependency** | Nguồn cung công việc do **lịch dự án của công ty** quyết · **Trưởng phòng Pháp chế duyệt lại** khi trường hợp khó tự quyết, khi lưỡng lự giữa quyền lợi các bên, hoặc khi liên quan quy định pháp luật · bản mẫu HĐMB (đổi khi luật đổi hoặc có dự án mới) |
| **Repeat condition** | Công ty có **dự án mới** · **luật thay đổi** dẫn tới mẫu HĐMB mới · hợp đồng cần soát lại sau khi sửa |

## 2. Kết luận cadence

**Dạng hành vi đã chọn: `workflow của team`** (có pha "theo dự án"). Không chọn "thói quen thường xuyên" vì công việc không do user tự khởi phát.

**Kết luận theo template:**

> Đối với **nhân viên Pháp chế tại sàn/chủ đầu tư bất động sản**, core action **chốt toàn bộ phát hiện rủi ro và xuất bản kết luận rà soát cho một hợp đồng** thường xuất hiện **trung bình 1–3 lần mỗi tuần, và ít nhất một tuần mỗi tháng không có hợp đồng nào** vì **hợp đồng đến từ kênh nội bộ mỗi khi công ty có dự án mới chứ không do họ tự khởi phát, và mỗi hợp đồng là một đơn vị công việc độc lập mất khoảng 1–2 giờ**. Do đó, nhịp đo phù hợp là **theo tuần cho NSM và engagement, và khung 4 tuần cho retention**, ở cấp **nhân viên Pháp chế (user)**.

### Vì sao tuần cho NSM, khung 4 tuần cho retention, không daily

- **Không daily:** 1–3 hợp đồng mỗi tuần nghĩa là phần lớn các ngày không có việc. DAU cho tín hiệu nhiễu và tạo áp lực sai: đẩy user vào app mỗi ngày không tạo thêm value nào.
- **NSM giữ theo tuần:** mỗi hợp đồng là một đơn vị công việc có deadline riêng, và lượng việc dao động theo lịch dự án. Đọc theo tuần mới thấy được dao động đó.
- **Retention dùng khung 4 tuần, không đọc một tuần đơn lẻ:** có ít nhất một tuần trống mỗi tháng. Nếu lấy đúng "tuần thứ 4" làm điểm đo, khoảng một phần tư reviewer đang dùng bình thường vẫn bị tính là mất. Khung 4 tuần phủ trọn một tuần trống nên không đọc nhầm.

### Frequency cao hơn có = value cao hơn không? → Không

- Số hợp đồng/tuần **do lịch dự án quyết định**, không phải thứ sản phẩm tự đẩy lên được → không dùng nó làm NSM thuần.
- Hướng tốt lên của sản phẩm này là **cùng độ phủ rủi ro nhưng ít công hơn** (dưới 1–2 giờ/hợp đồng), không phải Pháp chế ngồi trong app lâu hơn.

---

## 🚪 GATE 2 — cách bảo vệ

Chữ "vì" đứng được vì trigger là *hợp đồng đến từ kênh nội bộ khi có dự án mới* (đã xác minh qua phỏng vấn), nên nhịp đo phải khớp lịch dự án, không khớp thói quen cá nhân. Có số liệu mốc: 1–3 hợp đồng/tuần và ≥1 tuần trống/tháng — chính số liệu đó giải thích vì sao retention phải dùng khung 4 tuần thay vì một tuần đơn lẻ.

---

**Tiếp theo →** [03 — Metric System](../03/README.md)
