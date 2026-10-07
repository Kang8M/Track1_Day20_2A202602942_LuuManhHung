# AI Support Log

**Họ tên:** Lưu Mạnh Hùng · **MHV:** 2A202602942 · **Track 1 — Day 20**

---

## Khai báo trung thực về mức độ dùng AI

Brief cho phép dùng AI để brainstorm ứng viên core action, phản biện định nghĩa retention, gợi ý tên event; và **không** cho phép dùng AI để chọn thay core action, viết thay kết luận cadence / metric hypothesis / rationale.

**Mức độ thực tế trong bài này — ghi đúng như đã xảy ra:**

- Tôi tự quyết: **persona** (Nhân viên Pháp chế, sau khi AI chỉ ra rằng chọn cả Pháp chế + Sale là vi phạm yêu cầu "một persona thôi"), **góc core job** (góc rủi ro/sót điều khoản, chọn trong 3 góc AI đề xuất), **phạm vi use case** (chỉ HĐMB sơ cấp).
- **AI đã soạn bản nháp Phase 1–5**, bao gồm cả core action, kết luận cadence và metric hypothesis — là ba thứ brief yêu cầu phải do tôi viết. Tôi đã yêu cầu AI làm tiếp toàn bộ, nên khai báo rõ ở đây.
- Các quyết định lõi trong `metrics-pack.md` từng được đánh dấu để tôi duyệt. Tôi đã đọc và duyệt cả năm chỗ rồi bỏ các dấu đánh dấu.
- Tôi tự phỏng vấn một nhân viên Pháp chế (n=1) và dùng kết quả để thay các con số AI đưa ra. AI sửa lại các mục theo số phỏng vấn đó (retention khung 4 tuần, activation 14 ngày).
- Ba điểm yếu cuối (event của Sale, Engagement-frequency trùng NSM, retention cấp cá nhân) do AI xử lý theo yêu cầu "hoàn thiện bài lab" của tôi, không phải do tôi tự quyết từng điểm.
- Các đoạn trả lời ở câu 3 và ở phần "Điều tôi mang về" trong README tôi tham khảo mẫu do AI gợi ý, một số đoạn gần nguyên văn. Đoạn nhận định đầu câu 2 dựa trên một ý AI liệt kê, kèm kết quả phỏng vấn của tôi.

---

## AI đã giúp tôi ở đâu?


| Việc       | AI đã làm gì                                                                                                                                                                                    |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Đọc brief | Tổng hợp 11 file`docs/` thành `CHECKLIST.md` theo 6 phase + 5 gate                                                                                                                               |
| Phase 0     | Chỉ ra lỗi chọn 2 persona; đưa bảng so sánh core job của Pháp chế vs Sale; đề xuất 3 góc core job                                                                                     |
| Phase 1     | Liệt kê ứng viên core action và lập luận loại bỏ từng ứng viên (upload / AI sinh báo cáo / chốt một phát hiện)                                                                    |
| Phase 2     | Soạn Action Nature Card 8 trường; soạn kết luận cadence theo template                                                                                                                         |
| Phase 3     | Soạn activation, phân biệt Active/Activated, retention 6 thành phần, NSM theo công thức, 3 leading, 3 counter-metric                                                                         |
| Phase 4     | Vẽ loop 2 chu kỳ; soạn metric hypothesis; soạn bảng event + 3 acceptance criteria                                                                                                            |
| Phase 5     | Đối chiếu 7 câu tự soi; soạn revision log                                                                                                                                                     |
| Nghiệp vụ | Gợi ý các điểm rủi ro điển hình của HĐMB chung cư (diện tích thông thuỷ/tim tường, phí bảo trì 2%, chậm bàn giao, sở hữu chung chỗ đậu xe, điều kiện cấp sổ hồng) |
| Phỏng vấn | Soạn 6 câu hỏi phỏng vấn Pháp chế và danh mục 10 nhóm điều khoản trọng yếu để tôi chọn; sửa các mục theo số phỏng vấn của tôi |
| Reflection | Gợi ý khung và đoạn mẫu cho câu 3 và phần "Điều tôi mang về" trong README |

---

## AI sai, hời hợt hoặc đề xuất metric sai nature ở đâu?

**Nhận định của tôi** (nguyên văn từ phiếu làm việc):

> AI đưa "20–90 phút/hợp đồng", "10–20 hợp đồng/tuần", "đợt mở bán cách 4–8 tuần" như thể là dữ liệu, trong khi không có nguồn nào. Sau khi tôi phỏng vấn pháp chế thật thì dữ liệu thật là: trung bình từ 1-3 hợp đồng / tuần và thời gian xử lý mỗi hợp đồng giao động từ 1-2 giờ tùy theo mức độ phức tạp của hợp đồng.

**Các điểm AI tự nhận là yếu** (ghi lại để đối chiếu, kèm trạng thái xử lý):

1. **Không có dữ liệu thật nào đứng sau các con số nhịp.** "Vài lần mỗi tuần, có tuần 10–20 hợp đồng", "20–90 phút/hợp đồng", "đợt mở bán cách nhau 4–8 tuần" đều là **phỏng đoán**, chưa phỏng vấn một Pháp chế nào. Brief cấm bịa benchmark. → ✅ **Đã xử lý:** thay bằng số từ phỏng vấn 1 Pháp chế (n=1); gỡ hẳn con số "4–8 tuần".
2. **Mức độ "Cao" của phát hiện rủi ro được dùng khắp nơi nhưng chưa định nghĩa.** Toàn bộ completion rule, NSM và counter-metric đều dựa vào `severity='high'`, mà ai quyết định mức đó — AI hay Pháp chế? Nếu AI tự xếp mức thì NSM đang dựa vào output hệ thống, đúng cái bẫy Phase 1 cấm. → ✅ **Đã xử lý:** Rule-book 10 nhóm điều khoản, AI chỉ gán nhóm, Pháp chế được ghi đè (`severity_source`).
3. **Thư viện tiền lệ có thể chưa tồn tại trong sản phẩm.** Cả chu kỳ 2 của loop và leading indicator #3 đều dựa vào tính năng này. → ✅ **Đã xử lý:** xác nhận thư viện tiền lệ đã có trong sản phẩm.
4. **Retention ở cấp cá nhân có thể sai nature với sản phẩm B2B.** Pháp chế nghỉ việc/đổi phòng thì cohort cá nhân vỡ, trong khi công ty vẫn là khách hàng. AI đã ghi nhận hạn chế này nhưng không giải quyết. → ⚪ **Giữ có lý do:** persona đã chốt là cá nhân Pháp chế và họ là người ký tên; bản account-level ghi là việc chưa làm.
5. **`review_report_opened_by_sales` là event của một role không phải persona** — có thể bị coach bắt là lạc khỏi phạm vi đã chốt ở Phase 0. → ✅ **Đã xử lý:** bỏ event này (7 → 6 event).
6. **Engagement-frequency gần như trùng với NSM** (đều là số hợp đồng publish/tuần, khác ở mẫu số). Có thể là một metric bị đếm hai lần. → ✅ **Đã xử lý:** giữ cả hai nhưng phân biệt rõ: NSM ở cấp workspace, Frequency đọc phân bố theo từng reviewer.

---

## Tôi đã tự sửa hoặc quyết định lại điều gì?

AI tự nhận 3 điểm yếu nghiêm trọng và tôi xử lý cả 3. Số nhịp: tôi tự phỏng vấn một nhân viên Pháp chế thật và thay các con số AI đưa bằng số thật (1–3 hợp đồng/tuần, 1–2 giờ/hợp đồng). Mức "Cao": tôi chọn Rule-book 10 nhóm điều khoản để AI chỉ gán nhóm, không tự quyết mức. Thư viện tiền lệ: tôi xác nhận sản phẩm đã có nên loop có đủ 2 chu kỳ.

Sau khi đọc lại cả năm chỗ AI đánh dấu, tôi giữ nguyên vì ba ứng viên bị loại khớp với những gì tôi thấy ở dự án. Nhưng tôi sửa phần cadence vì số phỏng vấn cho thấy nhịp thật khác AI viết.

Core action là xuất bản kết luận cả hợp đồng, không phải chốt từng phát hiện, vì trách nhiệm của Pháp chế gắn với cả bản hợp đồng. Chốt 3 trên 20 phát hiện rồi bỏ dở thì hợp đồng vẫn chưa an toàn và người ký tên vẫn chịu rủi ro. Chốt từng phát hiện tôi giữ lại làm thước đo độ sâu, không dùng làm hành vi tạo giá trị.
