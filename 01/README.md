# 01 — Core Action Card (+ kết quả tự kiểm 5 tiêu chí)

> Phase 1 · 15 phút · [← Mục lục](../metrics-pack.md) · [← 00](../00/README.md)

## 1. Phân biệt bốn khái niệm

| Khái niệm | Câu hỏi | Trả lời cho dự án này |
| --- | --- | --- |
| **Core job** | User đang cố hoàn thành việc gì? | Không để sót điều khoản rủi ro trong HĐMB trước khi hợp đồng được đưa khách ký |
| **Core action** | User làm gì trong sản phẩm để tiến tới giá trị? | Chốt xử lý toàn bộ phát hiện rủi ro của một hợp đồng rồi **xuất bản kết luận rà soát** |
| **Core value** | User nhận được lợi ích gì? | Có cơ sở để khẳng định hợp đồng này đã được soát hết rủi ro trọng yếu → giảm xác suất sót và giảm phơi nhiễm trách nhiệm cá nhân |
| **Core value event** | Sự kiện nào chứng minh value đã xảy ra? | `contract_review_published` |

**Ba ứng viên bị loại khỏi vị trí core action — và vì sao:**

| Ứng viên bị loại | Vì sao loại |
| --- | --- |
| `contract_uploaded` (tải hợp đồng lên) | Là **đầu vào**, không phải giá trị. Upload 50 hợp đồng rồi không soát cái nào thì core job vẫn chưa xong. |
| AI sinh ra báo cáo rà soát | Là **output hệ thống** — đúng cái bẫy brief cấm. AI liệt kê 30 phát hiện không có nghĩa Pháp chế đã nhận được value; value chỉ xảy ra khi họ **phán quyết** từng phát hiện. |
| `risk_finding_resolved` (chốt một phát hiện) | Rất gần value nhưng là **sub-step**: chốt 3/20 phát hiện rồi bỏ dở thì hợp đồng vẫn chưa an toàn. → Giữ lại làm **thước đo depth** ở [mục 03](../03/README.md), không làm core action. |

## 2. Core Action Card

| Thành phần | Câu trả lời |
| --- | --- |
| **Target user** | Nhân viên Pháp chế tại sàn/chủ đầu tư, người ký nháy / duyệt nội dung pháp lý HĐMB sơ cấp |
| **Core job** | Không để sót điều khoản rủi ro trước khi hợp đồng được đưa khách ký |
| **Core action** | Chốt trạng thái cuối cho toàn bộ phát hiện rủi ro **mức Cao** của một hợp đồng, rồi xuất bản kết luận rà soát (redline/biên bản) cho bên Sale |
| **Object** | Một **bản hợp đồng HĐMB** (`contract_id`) và tập **phát hiện rủi ro** (`finding_id`) gắn với nó |
| **Preconditions** | Hợp đồng đã upload & parse thành công · AI đã sinh xong danh sách phát hiện · user có quyền duyệt hợp đồng đó |
| **Completion rule** | **100%** phát hiện mức Cao có trạng thái cuối — `accepted` kèm đề xuất sửa, hoặc `dismissed` kèm lý do — **VÀ** bản kết luận được đóng băng với timestamp + `reviewer_id`. **Mức Cao lấy từ Rule-book Pháp chế, không do AI tự quyết** (xem mục 4) |
| **Core value** | Pháp chế có cơ sở (và bằng chứng) rằng hợp đồng này đã được soát hết rủi ro trọng yếu |
| **Evidence of value** | Tồn tại một bản kết luận đã xuất bản, trong đó mọi phát hiện mức Cao đều có quyết định + lý do; Sale nhận và dùng được bản đó |
| **Candidate event** | `contract_review_published` (chính) · phụ trợ: `risk_finding_resolved`, `contract_uploaded`, `review_report_generated` |

## 3. Tự kiểm 5 tiêu chí

| # | Tiêu chí | Kết quả | Lập luận |
| --- | --- | --- | --- |
| 1 | Gần core value | ✅ Đạt | Hành vi xảy ra **chính là** value, không phải "tiến gần": hợp đồng đã được soát hết rủi ro trọng yếu |
| 2 | Có thể lặp lại | ✅ Đạt | Mỗi hợp đồng mới là một lần lặp — công ty có dự án mới, luật thay đổi dẫn tới mẫu HĐMB mới, hợp đồng cần soát lại sau khi sửa |
| 3 | Có thể quan sát | ✅ Đạt | Completion rule kiểm được bằng dữ liệu: `count(findings WHERE severity='high' AND status='open') = 0` và tồn tại bản ghi publish |
| 4 | Có ý nghĩa | ⚠️ **Đạt có điều kiện** | Số hợp đồng soát xong tăng chỉ tốt **nếu chất lượng soát không tụt**. Có đường game rõ ràng: bấm `dismissed` hàng loạt cho đủ điều kiện publish → **bắt buộc có counter-metric ở mục 03** |
| 5 | Có thể tác động | ✅ Đạt | Team cải thiện được: chất lượng phát hiện, xếp mức độ, gợi ý câu sửa sẵn, thư viện tiền lệ theo từng CĐT → giảm effort để đi tới publish |

**Kết quả: 5/5 đạt** (tiêu chí 4 đạt kèm điều kiện đã được xử lý bằng counter-metric ở [mục 03](../03/README.md)).

## 4. Định nghĩa mức "Cao" — ai xếp?

Completion rule, NSM và các counter-metric đều dựa vào mức Cao, nên mức này **không được do AI tự phán**. Nếu AI tự xếp mức thì NSM đổi mỗi khi đổi prompt, và đang đo output hệ thống chứ không đo hành vi của user.

**Cách chọn: Rule-book làm nền, Pháp chế được ghi đè.**

> `severity = 'high'` khi phát hiện thuộc **một trong các nhóm điều khoản trọng yếu** của **Rule-book Pháp chế** (có số phiên bản, do Trưởng phòng Pháp chế phê duyệt). **AI chỉ gán điều khoản vào nhóm, không tự quyết mức độ.** Pháp chế được nâng hoặc hạ mức kèm lý do; mỗi lần ghi đè được ghi nhận qua thuộc tính `severity_source` ∈ `{rulebook, reviewer_override}`.

**Danh mục nhóm điều khoản trọng yếu của HĐMB sơ cấp (10 nhóm):**

| # | Nhóm |
| --- | --- |
| 1 | Tiến độ và phương thức thanh toán |
| 2 | Thời điểm bàn giao + chế tài khi chậm bàn giao |
| 3 | Diện tích căn hộ — thông thuỷ vs tim tường + cách xử lý chênh lệch |
| 4 | Phí bảo trì 2% — ai thu, giữ ở đâu, bàn giao cho Ban quản trị khi nào |
| 5 | Sở hữu chung / sở hữu riêng — chỗ đậu xe, tầng thương mại, sân thượng |
| 6 | Cam kết cấp giấy chứng nhận (sổ hồng) + thời hạn + chế tài |
| 7 | Lãi chậm thanh toán và điều kiện đơn phương chấm dứt |
| 8 | Điều kiện chuyển nhượng hợp đồng |
| 9 | Điều khoản bất khả kháng |
| 10 | Cơ quan giải quyết tranh chấp |

**Phần còn phụ thuộc AI:** việc gán một điều khoản vào đúng nhóm vẫn là output của AI. Hai thứ kiểm soát nó: Pháp chế có quyền ghi đè, và tỉ lệ ghi đè cùng tỉ lệ cảnh báo sai là counter-metric ở [mục 03](../03/README.md). Phiên bản Rule-book và ngày ban hành do công ty xác định khi triển khai.

---

## 🚪 GATE 1 — cách bảo vệ nếu coach hỏi

Có actor (Pháp chế), object (bản hợp đồng + tập phát hiện), completion rule (100% findings mức Cao có trạng thái cuối + publish).

Không phải "mở app" vì mở app không tạo ra bản kết luận nào. Không phải "hỏi AI" vì AI trả lời xong mà Pháp chế chưa phán quyết thì hợp đồng vẫn chưa an toàn và trách nhiệm vẫn treo.

---

**Tiếp theo →** [02 — Action Nature Card + kết luận cadence](../02/README.md)
