# 06 — Tracking nhanh (6 events + 3 acceptance criteria)

> Phase 4 · ~7 phút · [← Mục lục](../metrics-pack.md) · [← 05](../05/README.md)

## Bảng core events

| Tên event | Ý nghĩa (điều ĐÃ xảy ra) | Thời điểm ghi nhận | Metric sử dụng |
| --- | --- | --- | --- |
| `contract_uploaded` | Một bản HĐMB đã được nạp và parse thành công | Khi parser trả về trạng thái thành công **và** văn bản đã lưu. Không ghi khi bấm nút chọn file, không ghi khi parse lỗi | Mẫu số của time-to-first-publish (leading #2); mẫu số của tỉ lệ hoàn tất rà soát |
| `review_report_generated` | AI đã sinh xong danh sách phát hiện rủi ro cho hợp đồng | Khi toàn bộ phát hiện đã lưu kèm mức độ và job = `completed` | Funnel upload→report→publish; chi phí LLM/hợp đồng (counter #3). **Không** dùng làm core action |
| `risk_finding_resolved` | Một phát hiện đã được Pháp chế chốt trạng thái cuối kèm lý do. Thuộc tính `severity_source` ∈ `{rulebook, reviewer_override}` cho biết mức độ lấy từ Rule-book hay do Pháp chế ghi đè | Khi trạng thái phát hiện chuyển từ `open` sang trạng thái cuối **và** lý do đã lưu | Engagement-depth; counter #1 (dismiss không lý do); counter #2 (cảnh báo sai); leading #1; tỉ lệ ghi đè mức độ (`reviewer_override`) làm tín hiệu về độ chính xác khi AI gán nhóm điều khoản |
| `contract_review_published`<br>**← core value event** | Pháp chế xuất bản kết luận; 100% phát hiện mức Cao đã có trạng thái cuối | Khi bản kết luận được đóng băng (timestamp + `reviewer_id`) **và** điều kiện 100% findings mức Cao đạt | **NSM (WCC)**; Activation event; Retention return event; Engagement-frequency |
| `review_precedent_saved` | Một điều khoản/câu sửa được lưu vào thư viện tiền lệ nội bộ | Khi bản ghi tiền lệ được tạo và gắn `clause_id` + `contract_id` | Leading #3 (saved state của loop) |
| `precedent_applied_to_finding` | Một phát hiện ở hợp đồng mới được xử lý bằng tiền lệ đã duyệt trước đó | Khi hệ thống khớp tiền lệ **và** Pháp chế chấp nhận áp dụng | Bằng chứng chu kỳ 2 của loop đang chạy; đầu vào cho metric hypothesis |

Mọi event đều map về ít nhất một metric ở [mục 03](../03/README.md) / [mục 04](../04/README.md) → không có event "track cho vui".

## Acceptance criteria

### AC-1 — chống ghi trùng ở core value event

> Với mỗi cặp `reviewer_id` và `contract_id`, hệ thống chỉ ghi `contract_review_published` khi bản kết luận chuyển từ trạng thái nháp sang đã xuất bản **VÀ** số phát hiện mức Cao còn trạng thái `open` bằng 0. Tải lại trang, gửi lại email hay mở lại bản đã publish **không** được tạo thêm event cho cùng lần xuất bản đó.

### AC-2 — chỉ bắn khi hành vi thật sự hoàn tất

> Với mỗi `finding_id`, `risk_finding_resolved` chỉ được ghi một lần cho mỗi lần chuyển trạng thái từ `open` sang trạng thái cuối, và phải kèm `resolution` (`accepted`/`dismissed`), `reason_text` khác rỗng và `severity_source`. **Autosave trong lúc Pháp chế đang gõ lý do không được bắn event.** Nếu phát hiện bị mở lại và chốt lần nữa, ghi một event mới kèm `resolution_round` tăng dần, không ghi đè event cũ.

### AC-3 — loại trừ và timezone

> Không ghi event cho tài khoản nội bộ (`is_internal=true`), tài khoản demo và job chạy thử của đội phát triển. Mọi event quy về tuần lịch theo timezone **Asia/Ho_Chi_Minh** để cohort theo tuần không bị lệch ngày.

---

## 🚪 GATE 5 (phần tracking) — cách bảo vệ

6 event (trong khoảng 4–8 brief yêu cầu), mỗi event map về ≥1 metric. 3 acceptance criteria, trong đó AC-1 và AC-2 nhắm đúng hai bẫy brief nêu: bắn khi mới bấm nút, và reload/autosave ghi trùng.

## ⬜ Chưa làm — không nhận là đã làm

Bản tracking đầy đủ theo **7 điều Metric Definition Contract (S47)**. Còn thiếu:
- `identity` — cách định danh user khi dùng SSO công ty
- Danh sách `properties` bắt buộc cho từng event
- Quy tắc versioning khi mẫu HĐMB của CĐT đổi

---

**Tiếp theo →** [Phase 5 — Tự soi lỗi & revision log](../metrics-pack.md#phase-5--tự-soi-7-lỗi-kinh-điển)
