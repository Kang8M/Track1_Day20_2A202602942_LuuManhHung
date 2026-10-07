# 05 — Product Loop (2 chu kỳ + metric hypothesis)

> Phase 4 · ~8 phút · [← Mục lục](../metrics-pack.md) · [← 04](../04/README.md)

**Loại loop chính đã chọn: `workflow`** — có thành phần `progress` ở phần thư viện tiền lệ tích luỹ.

Điều kiện để gọi là loop: **chu kỳ 2 phải rẻ hơn chu kỳ 1.**

**Thư viện tiền lệ đã có trong sản phẩm** (xác nhận của người làm dự án), nên chu kỳ 2 kiểm chứng được ngay, không phải giả thuyết phụ thuộc tính năng chưa phát hành.

**Rủi ro cần theo dõi:** mẫu HĐMB đổi khi luật đổi hoặc có dự án mới (phỏng vấn n=1, người trả lời nói không nắm rõ). Nếu tiền lệ gắn theo nguyên mẫu hợp đồng thì mẫu mới sẽ làm mất khớp. Tiền lệ cần gắn theo **từng điều khoản** để phần không đổi giữa hai mẫu vẫn tái dùng được.

## Chu kỳ 1

```
Natural trigger
  Công ty có dự án mới → hợp đồng đến qua kênh nội bộ
      ↓
Core action
  Pháp chế upload → chốt từng phát hiện rủi ro (accepted/dismissed + lý do)
  → xuất bản kết luận rà soát
      ↓
Immediate value
  Hợp đồng sạch rủi ro trọng yếu + có biên bản ghi rõ ai quyết định gì
  → giảm phơi nhiễm trách nhiệm cá nhân
      ↓
Saved state / investment
  Quyết định + lý do + câu sửa được lưu thành TIỀN LỆ NỘI BỘ
  Mẫu điều khoản đã duyệt của CĐT đó được ghi nhận
```

## Chu kỳ 2

```
Next natural trigger
  Dự án mới tiếp theo / luật đổi dẫn tới mẫu HĐMB mới / hợp đồng cần soát lại sau khi sửa
      ↓
Core action tiếp theo
  Upload hợp đồng mới → hệ thống TỰ KHỚP với tiền lệ đã duyệt
  → phần lớn phát hiện đã có câu trả lời sẵn, Pháp chế chỉ chốt phần mới
      ↓
Repeat value
  Soát xong NHANH HƠN chu kỳ trước với CÙNG độ phủ,
  và tin cậy hơn vì được neo vào tiền lệ chính công ty mình đã duyệt
      ↓
Saved state dày thêm → vòng sau càng rẻ
```

## Reason to return nếu bỏ hết notification

1. **Công việc tự đến từ bên ngoài** — công ty có dự án mới thì hợp đồng đến qua kênh nội bộ. Nhu cầu không do sản phẩm tạo ra, nên không cần notification để bịa ra nhịp quay lại.
2. **Thư viện tiền lệ chỉ nằm trong hệ thống** — soát hợp đồng ở ngoài là tự bỏ lợi thế đã tích luỹ, và mất luôn biên bản truy vết.

→ Đúng luật "nurture chỉ khuếch đại nature": notification ở đây chỉ để **nhắc deadline hợp đồng đang treo**, không phải lý do quay lại.

## Metric hypothesis

> Nếu loop này hoạt động, metric **retention khung 4 tuần (B1) của Pháp chế đã activated** (return event = `contract_review_published`) sẽ thay đổi theo hướng **tăng** trong **8 tuần kể từ khi thư viện tiền lệ được bật**, vì **mỗi hợp đồng đã soát làm giàu tiền lệ nội bộ, khiến hợp đồng kế tiếp tốn ít công hơn mà vẫn đạt completion rule — chi phí lặp lại giảm dần theo từng vòng**.

**Kiểm chứng kèm (để hypothesis không bị đọc lệch):** trong cùng 8 tuần, **median time-to-publish mỗi hợp đồng phải giảm** trong khi **số phát hiện mức Cao được chốt / hợp đồng không giảm**. Nếu time-to-publish giảm mà depth cũng giảm → loop không hoạt động, chỉ là Pháp chế đang soát nhanh cho xong.

---

## 🚪 GATE 4 (phần loop) — cách bảo vệ

Loop có 2 chu kỳ đầy đủ và chu kỳ 2 **rẻ hơn** chu kỳ 1 nhờ saved state. Hypothesis trỏ về đúng một metric đã định nghĩa ở [mục 04](../04/README.md). Không có streak, badge hay notification nào làm động lực.

---

**Tiếp theo →** [06 — Tracking nhanh](../06/README.md)
