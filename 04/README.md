# 04 — Retention Definition (6 thành phần)

> Phase 3 · 25 phút (cùng [mục 03](../03/README.md)) · [← Mục lục](../metrics-pack.md) · [← 03](../03/README.md)

## Sáu thành phần

| Thành phần | Định nghĩa | Vì sao chọn vậy |
| --- | --- | --- |
| **Unit** | Nhân viên Pháp chế (`reviewer_id`) | Là người thực hiện core action và chịu trách nhiệm cá nhân |
| **Cohort entry** | Tuần lịch user phát sinh `contract_review_published` **đầu tiên** | **Không** lấy tuần đăng ký: đăng ký chưa phải nhận value. Vào cohort ở mốc có value mới đọc được đường retention |
| **Return event** | `contract_review_published` | Chính core value event. Không phải `login`, không phải `contract_uploaded` |
| **Window** | **Khung 4 tuần**: B1 = tuần 1–4 sau tuần vào cohort, B2 = tuần 5–8, và cứ thế. Kèm lát cắt **project-based**: tính lại theo từng dự án mới của công ty | Khớp [mục 02](../02/README.md): mỗi Pháp chế có ít nhất một tuần trống mỗi tháng, nên một tuần đơn lẻ không đọc được. Khung 4 tuần phủ trọn một tuần trống |
| **Threshold** | **≥1** `contract_review_published` trong khung 4 tuần | Với 1–3 hợp đồng/tuần và tuần trống, một lần trong khung là mức tối thiểu hợp lý. Chưa đặt ngưỡng "nhiều lần" vì chưa có dữ liệu để biết bao nhiêu là bình thường |
| **Segment** | Pháp chế đã **activated**, tách theo loại tổ chức: sàn giao dịch vs chủ đầu tư | Nguồn cung công việc khác nhau thì retention không so được với nhau. Chưa tách theo khối lượng hợp đồng/tuần vì mức trung bình chỉ 1–3, chưa đủ chênh lệch để chia nhóm |

**Định nghĩa viết liền một câu (để dán vào dashboard):**

> **Retention khung 4 tuần (B1)** = tỉ lệ nhân viên Pháp chế **đã activated**, vào cohort ở **tuần có `contract_review_published` đầu tiên**, có **ít nhất 1** `contract_review_published` trong **bốn tuần liền sau tuần vào cohort** — tính **riêng theo từng loại tổ chức** (sàn giao dịch, chủ đầu tư).

## So retention với ba mốc (S34) — không so với con số cứng

| Mốc | Cách so |
| --- | --- |
| **Natural cycle** | Pháp chế nhận việc khi công ty có dự án mới, trung bình 1–3 hợp đồng/tuần, ít nhất một tuần trống mỗi tháng (phỏng vấn n=1). **Một tuần không có hợp đồng không phải churn.** Đọc retention theo khung 4 tuần liên tiếp (B1, B2, B3…), không đọc từng tuần |
| **Cohort đúng segment** | So Pháp chế sàn với Pháp chế sàn, Pháp chế chủ đầu tư với Pháp chế chủ đầu tư; so mỗi cohort với cohort trước của chính segment đó |
| **Benchmark category** | So với công cụ legal / document workflow B2B **khi có số liệu có nguồn**. Chưa có số nào, nên bài này không nêu con số benchmark. Không so với consumer app |

❌ Không đặt mục tiêu kiểu "retention B1 phải trên 40%" khi chưa đo được natural cycle của segment đó.

---

## 🚪 GATE 3 (phần retention) — cách bảo vệ

Đủ 6 thành phần. Window khung 4 tuần khớp kết luận cadence ở mục 02 và có căn cứ từ số liệu (≥1 tuần trống/tháng). Return event là core value event chứ không phải login.

## ⬜ Chưa làm — không nhận là đã làm

Bản retention ở **cấp account/công ty**. Sản phẩm hướng B2B, nên Pháp chế nghỉ việc hoặc đổi phòng sẽ làm vỡ cohort cá nhân trong khi công ty vẫn là khách hàng.

---

**Tiếp theo →** [05 — Product Loop](../05/README.md)
