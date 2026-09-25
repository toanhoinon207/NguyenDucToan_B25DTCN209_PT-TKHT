# Phần 1 — Class Diagram cho nghiệp vụ Đặt lịch hẹn

## 1. Xác định thuộc tính Class

**Class KhachHang:**

Thuộc tính:

1. maKhachHang
2. tenKhachHang

**Class KyThuatVien:**

Thuộc tính:

1. maKTV
2. tenKTV

**Class LichHen:**

Thuộc tính:

1. maLichHen
3. khungGio
4. ngayHen

## 2. Vẽ Class Diagram

# Phần 2 — Điều kiện dữ liệu hợp lệ

**Điều kiện dữ liệu hợp lệ:**

1. `maLichHen` không được trùng
2. `ngayHen` và `khungGio` không được là thời gian đã qua
3. Cùng 1 KTV không được trùng `khungGio` của `LichHen` mới

# Phần 3 — Sequence Diagram + Xử lý trường hợp lỗi + Trình bày kết quả theo mẫu chung

## 1. Vẽ Sequence Diagram

## 2. Hủy lịch hẹn — Trường hợp mã lịch hẹn không tồn tại:

1. Khách hàng gửi yêu cầu hủy lịch hẹn bằng mã lịch hẹn.
2. HeThong tìm kiếm lịch hẹn theo mã được cung cấp.
3. Không tìm thấy lịch hẹn -> Trả về thông báo lỗi "Không tìm thấy lịch hẹn".

## 3. Kết quả theo mẫu chung
**Ví dụ 1 – Đặt lịch thành công**

- Trạng thái: THÀNH CÔNG
- Dữ liệu trả về: LH003 - KTV Hùng - 10:00 - 11:00, 20/03/2026 - Nguyễn Văn C
- Thông báo lỗi:

**Ví dụ 2 – Đặt lịch bị từ chối**

- Trạng thái: TỪ CHỐI
- Dữ liệu trả về:
- Thông báo lỗi: Trùng khung giờ kỹ thuật viên