# Metrics Pack — AI rà soát hợp đồng mua bán nhà chung cư

**Họ tên:** Lưu Mạnh Hùng · **MHV:** 2A202602942 · **Track 1 — Day 20**

> **Trạng thái bản này:** đã duyệt. Phạm vi (persona, góc core job, thị trường sơ cấp) do tôi quyết, kèm số liệu từ một buổi phỏng vấn nhân viên Pháp chế (n=1). Phần soạn thảo Phase 1–5 có dùng AI, kể cả ba thứ brief yêu cầu phải tự viết (core action, kết luận cadence, metric hypothesis); tôi đã đọc và duyệt cả năm chỗ quyết định lõi. Khai báo đầy đủ trong [`ai-support-log.md`](./ai-support-log.md).

**Bản một trang (HTML, có link chia sẻ):** https://claude.ai/artifact/7hnSd4GzshLfmnwU5T3aJS · nguồn: [`metrics-pack.html`](./metrics-pack.html)

---

## Mục lục

| Mục | Nội dung | Gate |
| --- | --- | --- |
| [**00**](./00/README.md) | Dự án, persona, core job | — |
| [**01**](./01/README.md) | Core Action Card + kết quả tự kiểm 5 tiêu chí | Gate 1 |
| [**02**](./02/README.md) | Action Nature Card + kết luận cadence | Gate 2 |
| [**03**](./03/README.md) | Metric System — activation / engagement / NSM / leading / counter | Gate 3 |
| [**04**](./04/README.md) | Retention Definition — 6 thành phần | Gate 3 |
| [**05**](./05/README.md) | Product Loop — 2 chu kỳ + metric hypothesis | Gate 4 |
| [**06**](./06/README.md) | Tracking nhanh — 6 events + 3 acceptance criteria | Gate 5 |
| ↓ dưới đây | Phase 5 — tự soi 7 lỗi + revision log | Gate 5 |

## Chuỗi quyết định xuyên suốt

Mỗi mục dùng lại kết quả mục trước — đây là tiêu chí "HOÀN TẤT" của bài:

```
Core job: "sót một điều khoản là tôi chịu trách nhiệm"          [00]
  → Core action: xuất bản kết luận rà soát một hợp đồng          [01]
    → Nhịp: NSM theo tuần, retention khung 4 tuần (việc đến từ kênh nội bộ khi có dự án mới)  [02]
      → NSM: Weekly Cleared Contracts (có quality threshold độ phủ)       [03]
      → Retention: khung 4 tuần, return event = contract_review_published [04]
        → Loop workflow+progress, chu kỳ 2 rẻ hơn nhờ thư viện tiền lệ    [05]
          → 6 event, mỗi event map về một metric ở trên                   [06]
```

**Tóm tắt một dòng mỗi quyết định lõi:**

| | |
| --- | --- |
| Persona | Nhân viên Pháp chế tại sàn/chủ đầu tư (Sale = bên liên quan) |
| Core action | Chốt 100% phát hiện mức Cao của một hợp đồng + xuất bản kết luận |
| Core value event | `contract_review_published` |
| Dạng hành vi | Workflow của team, pha theo dự án |
| Cadence | NSM theo tuần, retention khung 4 tuần, ở cấp user. Mốc: 1–3 hợp đồng/tuần, ≥1 tuần trống/tháng (phỏng vấn n=1) |
| Activation | `contract_review_published` lần đầu trong 14 ngày |
| NSM | Weekly Cleared Contracts (unit + quality threshold + weekly) |
| Retention | Khung 4 tuần (B1), unit = reviewer, cohort entry = tuần publish đầu tiên |
| Mức "Cao" | Lấy từ Rule-book Pháp chế (10 nhóm điều khoản), AI chỉ gán nhóm; Pháp chế được ghi đè |
| Counter-metric chính | Tỉ lệ `dismissed` không lý do trên phát hiện mức Cao |

---

## Phase 5 — Tự soi 7 lỗi kinh điển

| Câu tự soi | Kết quả | Căn cứ |
| --- | --- | --- |
| Core action không phải thao tác giao diện hay output hệ thống? | ✅ | Đã loại tường minh 3 ứng viên: upload (đầu vào), AI sinh báo cáo (output hệ thống), chốt một phát hiện (sub-step) — [mục 01](./01/README.md) |
| Activation không phải "xem hết hướng dẫn" hay "đăng nhập"? | ✅ | Activation = `contract_review_published` lần đầu trong 14 ngày; bản "Activated" còn đòi ≥1 phát hiện mức Cao được `accepted` — [mục 03](./03/README.md) |
| Frequency không cao hơn nhu cầu thật? | ✅ | Mốc thật 1–3 hợp đồng/tuần nên không daily; NSM theo tuần, retention khung 4 tuần; lập luận "số hợp đồng/tuần do lịch dự án quyết định" — [mục 02](./02/README.md) |
| Loop có reason to return ngoài notification? | ✅ | Hai lý do: hợp đồng đến qua kênh nội bộ khi có dự án mới, và thư viện tiền lệ bị khoá trong hệ thống — [mục 05](./05/README.md) |
| Retention không dùng chung một window cho mọi cadence? | ✅ | Window = khung 4 tuần (vì có ≥1 tuần trống/tháng) **kèm** lát cắt theo dự án mới; không dùng chung window tuần cho mọi mục — [mục 04](./04/README.md) |
| Mọi event đều map về một metric? | ✅ | Cột cuối bảng events ở [mục 06](./06/README.md) — không ô nào trống |
| Metric nào cũng có event để tính nó? | ✅ | Đã **bỏ** ứng viên NSM "số giờ tiết kiệm" vì không có event nào tính trung thực được nó |

---

## Revision log

Theo yêu cầu Phase 5 — mỗi dòng là một lựa chọn đã cân nhắc rồi đổi hoặc giữ:

1. **Đổi core action từ clause-level sang contract-level.** Ban đầu xét `risk_finding_resolved` (chốt một phát hiện) vì nó lặp nhiều và dễ đo. Đổi sang "xuất bản kết luận một hợp đồng" vì chốt 3/20 phát hiện rồi bỏ dở thì core job vẫn chưa xong — không đạt tiêu chí "gần core value". Clause-level được giữ lại làm thước đo **depth** ở mục 03.
2. **Không chọn daily cadence dù sản phẩm là công cụ làm việc hàng ngày.** Lý do: hợp đồng đến từ kênh nội bộ khi có dự án mới, trung bình 1–3 hợp đồng/tuần (phỏng vấn n=1). Đẩy Pháp chế vào app mỗi ngày không tạo thêm value nào.
3. **Thêm quality threshold vào định nghĩa Activated** (≥1 phát hiện mức Cao được `accepted`) sau khi nhận ra bản "publish ≥2 hợp đồng" đơn thuần vẫn đếm được người `dismissed` sạch mọi phát hiện cho xong.
4. **Loại ứng viên NSM "số giờ tiết kiệm"** — nghe đúng với core job nhưng vi phạm luật "metric nào cũng phải có event để tính nó".
5. **Giữ unit retention ở cấp cá nhân, không cấp account**, dù sản phẩm hướng B2B. Lý do: persona đã chốt ở Phase 0 là cá nhân Pháp chế và họ là người chịu trách nhiệm ký tên. Bản account-level được ghi nhận là **việc chưa làm**, không nhận là đã làm.
6. **Thay các con số nhịp phỏng đoán bằng số từ phỏng vấn một Pháp chế thật (n=1).** Bản đầu có "20–90 phút/hợp đồng", "10–20 hợp đồng/tuần", "đợt mở bán cách 4–8 tuần" do AI đưa ra không có nguồn, đúng loại brief cấm. Số thật: 1–3 hợp đồng/tuần, 1–2 giờ/hợp đồng, ≥1 tuần trống/tháng. Con số "4–8 tuần" gỡ hẳn vì không có dữ liệu thay thế. Giới hạn: chỉ một người, cần đo lại khi có dữ liệu sản phẩm.
7. **Đổi retention từ "đúng tuần thứ 4" sang khung 4 tuần.** Với ≥1 tuần trống/tháng, một điểm đo đơn lẻ sẽ tính nhầm khoảng một phần tư reviewer đang dùng bình thường là đã mất. Kéo theo: bỏ ngưỡng "≥2/tuần" và segment "<3 vs ≥3 hợp đồng/tuần" vì mức trung bình chỉ 1–3, chia nhóm không còn ý nghĩa.
8. **Đổi activation window từ 7 sang 14 ngày, và Activated từ 14 sang 30 ngày.** Cùng lý do tuần trống: cửa sổ 7 ngày có thể rơi đúng vào tuần không có hợp đồng.
9. **Định nghĩa mức "Cao" theo Rule-book Pháp chế (10 nhóm điều khoản), AI chỉ gán nhóm.** Bản đầu để AI ngầm tự xếp mức, nghĩa là NSM đo output hệ thống. Thêm thuộc tính `severity_source` để theo dõi tỉ lệ ghi đè.
10. **Gỡ câu "retention cao" khỏi mục benchmark** vì là khẳng định không nguồn. Chưa nêu con số benchmark nào.
11. **Sửa trigger từ "Sale/CĐT đẩy sang" thành "kênh nội bộ khi có dự án mới"** theo đúng câu trả lời phỏng vấn; người gửi cụ thể chưa xác minh.
12. **Bỏ event `review_report_opened_by_sales` (7 → 6 event).** Event này là hành vi của Sale, không phải persona đã chốt ở Phase 0, và nó trỏ tới một counter-metric "báo cáo bị bỏ qua" chưa từng được định nghĩa ở mục 03. Vi phạm luật mọi event phải map về một metric đã có.
13. **Giữ Engagement-frequency bên cạnh NSM nhưng phân biệt rõ.** NSM là tổng hợp đồng đã soát xong ở cấp workspace, có quality threshold; Frequency đọc phân bố theo từng reviewer (trung vị hợp đồng/reviewer/tuần, % reviewer có ≥1 hợp đồng trong tuần). Hai metric trả lời hai câu hỏi khác nhau.

---

## Sáu điểm yếu tự nhận — trạng thái

| # | Điểm yếu | Trạng thái |
| --- | --- | --- |
| 1 | Các con số nhịp là phỏng đoán không nguồn | ✅ **Đã xử lý** — thay bằng số từ phỏng vấn 1 Pháp chế (revision #6). Còn giới hạn n=1 |
| 2 | Mức "Cao" chưa định nghĩa ai xếp | ✅ **Đã xử lý** — Rule-book 10 nhóm, AI chỉ gán nhóm (revision #9). Còn phụ thuộc độ chính xác khi AI gán nhóm, kiểm soát bằng ghi đè và counter-metric |
| 3 | Thư viện tiền lệ có thể chưa tồn tại | ✅ **Đã xử lý** — người làm dự án xác nhận đã có. Rủi ro còn lại: tiền lệ phải gắn theo điều khoản, không theo nguyên mẫu |
| 4 | Retention cấp cá nhân có thể sai nature với B2B | ⚪ **Giữ có lý do** — persona đã chốt là cá nhân Pháp chế và họ là người ký tên (revision #5). Bản account-level là việc chưa làm |
| 5 | `review_report_opened_by_sales` là event của role không phải persona | ✅ **Đã xử lý** — bỏ event (revision #12) |
| 6 | Engagement-frequency gần trùng NSM | ✅ **Đã xử lý** — giữ cả hai, phân biệt cấp workspace và cấp reviewer (revision #13) |
