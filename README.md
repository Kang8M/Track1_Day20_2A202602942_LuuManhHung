# Track1_Day20_2A202602942_LuuManhHung

**Họ tên:** Lưu Mạnh Hùng · **MHV:** 2A202602942 · **Track 1 — Day 20: Product Metrics**

---

## Dự án chọn làm

**AI rà soát hợp đồng mua bán nhà chung cư (HĐMB)** — người dùng tải hợp đồng lên, hệ thống trả về báo cáo rà soát: điều khoản rủi ro, mức độ, giải thích, đề xuất sửa.

- **Use case chính:** HĐMB căn hộ chung cư **sơ cấp** (chủ đầu tư bán cho khách), soát trước khi đưa khách ký
- **Persona:** Nhân viên Pháp chế tại sàn giao dịch / chủ đầu tư
- **Core action:** Chốt toàn bộ phát hiện rủi ro mức Cao của một hợp đồng rồi xuất bản kết luận rà soát
- **Cadence:** NSM đọc theo tuần, retention đọc theo khung 4 tuần. Mốc từ phỏng vấn 1 Pháp chế: 1–3 hợp đồng/tuần, 1–2 giờ/hợp đồng, ít nhất một tuần trống mỗi tháng
- **Mức "Cao":** lấy từ Rule-book Pháp chế (10 nhóm điều khoản trọng yếu), AI chỉ gán nhóm, không tự quyết mức
- **NSM:** Weekly Cleared Contracts — số hợp đồng được xuất bản kết luận mỗi tuần, trong đó 100% phát hiện mức Cao có quyết định kèm lý do

---

## Link tệp Metrics Pack

👉 **https://claude.ai/artifact/7hnSd4GzshLfmnwU5T3aJS**

Mục lục bản markdown: [`metrics-pack.md`](./metrics-pack.md) · bản HTML nguồn: [`metrics-pack.html`](./metrics-pack.html)

### Cấu trúc tệp


| Mục | Nội dung                                                          | File                                   |
| ------ | -------------------------------------------------------------------- | ---------------------------------------- |
| `00` | Dự án, persona, core job                                         | [`00/README.md`](./00/README.md)       |
| `01` | Core Action Card + kết quả tự kiểm 5 tiêu chí                | [`01/README.md`](./01/README.md)       |
| `02` | Action Nature Card + kết luận cadence                            | [`02/README.md`](./02/README.md)       |
| `03` | Metric System — activation / engagement / NSM / leading / counter | [`03/README.md`](./03/README.md)       |
| `04` | Retention Definition — 6 thành phần                             | [`04/README.md`](./04/README.md)       |
| `05` | Product Loop — 2 chu kỳ + metric hypothesis                      | [`05/README.md`](./05/README.md)       |
| `06` | Tracking — 6 events + 3 acceptance criteria                       | [`06/README.md`](./06/README.md)       |
| —   | Phase 5 tự soi + revision log + 6 điểm yếu                     | [`metrics-pack.md`](./metrics-pack.md) |

---

## Điều tôi mang về áp dụng cho dự án thật

Trước bài này, tôi định đo hiệu quả bằng số báo cáo AI sinh ra hoặc số hợp đồng được tải lên. Cả hai đều là output của hệ thống chứ không phải việc người dùng nhận được giá trị. Giờ tôi đo số hợp đồng mà Pháp chế đã phán quyết hết các phát hiện mức Cao và xuất bản kết luận, vì chỉ lúc đó trách nhiệm của họ mới được giải quyết.

Buổi phỏng vấn cho thấy nhịp thật khác tôi tưởng: mỗi Pháp chế chỉ có 1–3 hợp đồng mỗi tuần và ít nhất một tuần trống mỗi tháng. Vì vậy tôi bỏ ý định đo hàng ngày, đọc NSM theo tuần và đọc retention theo khung 4 tuần để không tính nhầm người dùng bình thường là đã bỏ đi.

Việc tôi làm trước là xây Rule-book 10 nhóm điều khoản, vì metric chính phụ thuộc vào chúng. Việc tôi hoãn là bảng thống kê số lượt dùng, vì chúng không di chuyển metric nào trong bài.

---

## Khai báo dùng AI

Xem [`ai-support-log.md`](./ai-support-log.md). Tôi tự quyết persona, góc core job, phạm vi use case và cách định nghĩa mức "Cao" (Rule-book), đồng thời tự phỏng vấn một nhân viên Pháp chế (n=1) để thay các con số AI đưa ra. AI soạn bản nháp Phase 1–5, kể cả core action, kết luận cadence và metric hypothesis, theo yêu cầu của tôi; tôi đã đọc và duyệt các phần đó. Các đoạn trả lời ở phần "Điều tôi mang về" và trong AI Support Log tôi tham khảo mẫu do AI gợi ý, một số đoạn gần nguyên văn.
