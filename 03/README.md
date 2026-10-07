# 03 — Metric System (activation / engagement / NSM / leading / counter)

> Phase 3 · 25 phút (cùng [mục 04](../04/README.md)) · [← Mục lục](../metrics-pack.md) · [← 02](../02/README.md)

## 1. Activation metric

| Thành phần | Định nghĩa |
| --- | --- |
| **Start event** | `workspace_joined` — tài khoản Pháp chế vào workspace của công ty lần đầu |
| **Activation event** | `contract_review_published` **lần đầu** — đã đi hết một vòng giá trị thật: upload → có phát hiện → chốt từng phát hiện → xuất bản kết luận |
| **Time window** | **14 ngày** kể từ `workspace_joined` |

**Vì sao 14 ngày, không phải 7:** theo phỏng vấn ([mục 02](../02/README.md)), mỗi Pháp chế nhận trung bình 1–3 hợp đồng/tuần và ít nhất một tuần mỗi tháng không có hợp đồng nào. Cửa sổ 7 ngày có thể rơi đúng vào tuần trống và đếm nhầm người dùng bình thường là chưa activate. 14 ngày đủ phủ một tuần trống mà vẫn ngắn để còn phân biệt được tác dụng của onboarding. Con số này dựa trên n=1, điều chỉnh khi có dữ liệu thật.

### Active ≠ Activated (S26)

| | Định nghĩa |
| --- | --- |
| **Active** (weekly) | Có ≥1 `contract_review_published` trong tuần lịch |
| **Activated** | Publish ≥**2** hợp đồng trong **30 ngày** đầu, **trong đó ≥1 hợp đồng có ≥1 phát hiện mức Cao được `accepted`** |

Điều kiện "≥1 phát hiện mức Cao được `accepted`" là **quality threshold của activation**: nó loại trường hợp user publish cho xong bằng cách `dismissed` sạch mọi phát hiện — người đó "active" nhưng chưa bao giờ thực sự nhận giá trị rà soát.

❌ **Không dùng làm activation:** "xem hết hướng dẫn", "đăng nhập", "upload hợp đồng đầu tiên" — cả ba đều xảy ra trước khi Pháp chế chạm vào core value.

## 2. Engagement metric (chọn tối đa 2 góc)

| Góc | Metric | Vì sao chọn |
| --- | --- | --- |
| **Frequency** | Số hợp đồng được xuất bản kết luận / Pháp chế / tuần | Khớp cadence weekly ở mục 02 |
| **Depth** | Số phát hiện mức Cao được chốt kèm lý do / mỗi hợp đồng | Đo "soát sâu" thật — phân biệt soát kỹ với soát cho xong |

**Bỏ `breadth`** vì bài chỉ phân tích một use case (HĐMB sơ cấp); đo breadth lúc này sẽ là metric không có quyết định nào đi kèm.

**Frequency khác NSM ở đâu:** NSM là tổng số hợp đồng đã soát xong ở cấp toàn workspace, có quality threshold. Frequency đọc phân bố theo từng reviewer: trung vị số hợp đồng/reviewer/tuần và tỉ lệ reviewer có ít nhất 1 hợp đồng trong tuần. NSM cho biết sản phẩm tạo ra bao nhiêu giá trị; Frequency cho biết giá trị đó dàn đều hay dồn vào vài người. Hai câu hỏi khác nhau nên giữ cả hai.

## 3. North Star Metric

**NSM — Weekly Cleared Contracts (WCC):**

> **Số hợp đồng HĐMB được Pháp chế xuất bản kết luận rà soát mỗi tuần, trong đó 100% phát hiện mức Cao đều có quyết định kèm lý do.**

| Thành phần công thức | Nội dung |
| --- | --- |
| **Unit of value** | Một hợp đồng được soát xong (contract cleared) |
| **Quality threshold** | 100% phát hiện mức Cao có quyết định **kèm lý do** — không có findings mức Cao bị để trống hay `dismissed` không lý do. **Mức Cao lấy từ Rule-book Pháp chế, không do AI tự quyết** ([mục 01](../01/README.md)) |
| **Frequency** | Mỗi tuần |

**Cách đọc:** ở cấp toàn workspace thì đọc theo tuần. Ở cấp từng reviewer, mỗi người chỉ có 0–3 hợp đồng/tuần và ít nhất một tuần trống mỗi tháng, nên đọc theo **trung bình trượt 4 tuần** để tuần trống không bị hiểu nhầm là tụt.

### Ba ứng viên NSM bị loại

- **"Số lượt hỏi AI" / "số hợp đồng upload"** — số lượng thuần, không có quality threshold, game được bằng cách upload hàng loạt.
- **"Số giờ tiết kiệm"** — nghe đúng với core job nhưng không có event nào tính được nó một cách trung thực (vi phạm luật: metric nào cũng phải có event để tính).
- **Doanh thu** — không phản ánh value user nhận được.

## 4. Leading indicators (tối đa 3)

| # | Leading indicator | Vì sao tin nó dự báo được core action lặp lại |
| --- | --- | --- |
| 1 | **Tỉ lệ phát hiện mức Cao được `accepted`** trong tuần đầu | Nếu Pháp chế chấp nhận phát hiện của AI thay vì bỏ qua, nghĩa là báo cáo đúng chuyên môn. Niềm tin vào chất lượng phát hiện là **điều kiện cần** để họ mang hợp đồng tiếp theo vào hệ thống thay vì mở Word |
| 2 | **Time-to-first-publish** (số giờ từ `contract_uploaded` → `contract_review_published`) | Rà soát hợp đồng luôn có deadline kinh doanh. Nếu lần đầu đã kịp deadline thì lần sau họ còn chọn dùng công cụ; nếu chậm hơn đọc tay thì họ quay về cách cũ ngay |
| 3 | **Số điều khoản được lưu vào thư viện tiền lệ mỗi tuần** | Đây là saved state của loop. Càng nhiều tiền lệ thì hợp đồng sau càng tốn ít công mà vẫn đạt completion rule → chi phí lặp lại giảm, nên nó dự báo việc core action tái diễn |

## 5. Counter-metrics

| # | Counter-metric | Chặn đường game nào |
| --- | --- | --- |
| 1 | **Tỉ lệ `dismissed` KHÔNG lý do trên phát hiện mức Cao** | Chặn trực tiếp cách game NSM: bấm bỏ qua hàng loạt cho đủ điều kiện publish. NSM tăng mà metric này tăng theo = số liệu rỗng |
| 2 | **Tỉ lệ cảnh báo sai** = phát hiện bị `dismissed` với lý do "không phải rủi ro" / tổng phát hiện | Chặn cách game độ phủ: cảnh báo mọi điều khoản để chắc chắn không sót. Độ phủ 100% nhưng Pháp chế mất niềm tin và bỏ qua cả báo cáo |
| 3 | **Chi phí LLM mỗi hợp đồng** | Chặn việc mua độ phủ bằng cách chạy mô hình ngày càng đắt — tăng NSM nhưng phá đơn vị kinh tế |

---

## 🚪 GATE 3 (phần metric) — cách bảo vệ

Activation có đủ start event + activation event + window 14 ngày. NSM đủ 3 thành phần của công thức. Có 3 counter-metric, trong đó #1 nhắm đúng đường game của chính NSM.

---

**Tiếp theo →** [04 — Retention Definition](../04/README.md)
