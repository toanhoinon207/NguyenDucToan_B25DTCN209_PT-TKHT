# Phần 1 – Hai phương án luồng thông điệp

## Phương án A – Tra cứu trực tiếp CSDL

**Chuỗi thông điệp:**

- TrackingPortalUI --> WaybillDB: track_waybill(waybill_code) — Sync
- WaybillDB --> TrackingPortalUI: Kết quả vị trí vận đơn — Return

## Phương án B – Tra cứu qua CacheService

**Chuỗi thông điệp:**

- TrackingPortalUI --> CacheService: track_waybill(waybill_code) — Sync

**Cache có dữ liệu:**

- CacheService --> TrackingPortalUI: Kết quả vị trí vận đơn — Return

**Cache không có dữ liệu:**

- CacheService --> WaybillDB: track_waybill(waybill_code) — Sync
- WaybillDB --> CacheService: Kết quả vị trí vận đơn — Return
- CacheService --> TrackingPortalUI: Kết quả vị trí vận đơn — Return

# Phần 2 – Bảng so sánh

| Tiêu chí | Phương án A: Trực tiếp DB | Phương án B: Qua CacheService |
|---|---|---|
| **Tốc độ phản hồi** | **Ưu:** Luồng ngắn, chỉ cần gọi DB và nhận kết quả. **Nhược:** Mỗi lượt tra cứu đều phải truy cập DB, dễ gây tải lớn khi cao điểm. | **Ưu:** Nếu dữ liệu đã có trong cache thì trả về rất nhanh, giảm số lần truy cập DB. **Nhược:** Nếu cache không có dữ liệu thì phải qua thêm CacheService rồi mới đến DB. |
| **Độ phức tạp luồng thông điệp** | **Ưu:** Đơn giản, chỉ gồm 1 Sync + 1 Return. | **Nhược:** Phức tạp hơn vì có thêm CacheService và phải xử lý trường hợp có/không có cache. **Ưu:** Có thể giảm tải cho DB nhờ xử lý các lượt tra cứu lặp lại ở cache. |

# Kết luận

**Phương án B – sử dụng CacheService** phù hợp hơn với bối cảnh **cao điểm**.

Lý do: dù luồng có thêm một đối tượng trung gian, khi dữ liệu đã có trong cache thì `TrackingPortalUI` nhận kết quả ngay mà **không cần chờ WaybillDB**. Điều này giúp giảm số lượt truy vấn trực tiếp vào CSDL khi có nhiều khách hàng tra cứu cùng lúc.