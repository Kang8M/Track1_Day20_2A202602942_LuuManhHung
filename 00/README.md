# 00 — Dự án, persona, core job

> Phase 0 · 10 phút · [← Mục lục](../metrics-pack.md)

## Dự án

**AI rà soát hợp đồng mua bán nhà chung cư (HĐMB)** — người dùng tải hợp đồng (PDF/Word) lên, hệ thống trả về **báo cáo rà soát**: danh sách điều khoản rủi ro, xếp mức độ, giải thích vì sao rủi ro, và đề xuất sửa.

## Use case chính được chọn để đào sâu

Rà soát **HĐMB căn hộ chung cư sơ cấp** (chủ đầu tư bán cho khách) **trước khi hợp đồng được đưa khách ký**.

✅ **Phạm vi đã chốt:** chỉ xét thị trường **sơ cấp** (chủ đầu tư → khách). Không xét hợp đồng chuyển nhượng thứ cấp — điều khoản và rủi ro khác hẳn (sổ hồng, công nợ, điều kiện chuyển nhượng). Lý do giữ hẹp: brief yêu cầu "chọn một use case chính, không phân tích toàn bộ sản phẩm".

## Persona (MỘT persona)

**Nhân viên Pháp chế** tại sàn giao dịch / chủ đầu tư bất động sản — người trực tiếp rà soát và chịu trách nhiệm về nội dung pháp lý của HĐMB trước khi hợp đồng ra khỏi tay mình.

- **Bên liên quan (không phải persona):** Sale bất động sản — người **nhận** kết quả rà soát để làm việc với khách. Được ghi ở trường `Dependency` của Action Nature Card ([mục 02](../02/README.md)).

## Core job

Viết bằng lời người dùng (không mô tả bằng tính năng):

> **"Tôi phải đọc hàng chục trang hợp đồng trong vài tiếng. Chỉ cần sót một điều khoản là công ty chịu rủi ro, và người chịu trách nhiệm là tôi."**

**Góc đã chọn:** rủi ro & sót điều khoản — không phải góc tiết kiệm thời gian, cũng không phải góc truy vết.

### Hệ quả đã khoá cho các phase sau

- Core value đi theo hướng **độ phủ rủi ro / không bỏ sót**, không phải "nhanh hơn".
- NSM bắt buộc có **quality threshold** về độ phủ, không được là số lượng hợp đồng thuần.
- Counter-metric ứng viên rõ ràng: **tỉ lệ cảnh báo sai** — nếu hệ thống cảnh báo mọi điều khoản thì độ phủ đạt 100% nhưng Pháp chế mất niềm tin và bỏ qua báo cáo.

---

**Tiếp theo →** [01 — Core Action Card](../01/README.md)
