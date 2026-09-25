# Phần 1 - Phân tích cơ chế phòng ngừa lỗi

## 1. Phân cấp 2 nút thao tác

- **Xác nhận đơn:** sử dụng Primary Button màu xanh, kích thước nổi bật -> thể hiện đây là hành động chính.
- **Hủy đơn hàng:** sử dụng Secondary/Text Button màu trung tính, không nổi bật như nút xác nhận -> giảm khả năng Seller bấm nhầm.
- Hai nút vẫn được đặt cạnh nhau nhưng có khác biệt rõ về màu sắc và mức độ nổi bật.

## 2. Cách Modal Window ngăn Seller hủy nhầm

| Thành phần | Cách phòng ngừa lỗi |
|---|---|
| **Modal Window** | Tạo thêm một bước xác nhận, ngăn việc hủy đơn ngay lập tức khi bấm nhầm. |
| **Dropdown List** | Bắt Seller phải chọn **lý do hủy** trước khi thực hiện. |
| **Xác nhận hủy** | Nút **màu đỏ**, thể hiện đây là hành động nguy hiểm. |
| **Trạng thái ban đầu** | Nút **“Xác nhận hủy” bị vô hiệu hóa** khi chưa chọn lý do. |
| **Đóng** | Cho phép Seller thoát Modal mà không hủy đơn. |

# Phần 2 - Thiết kế trên Wireframe Figma

https://www.figma.com/design/4QzkJmwyAMSjZLfYgRKHUx/Untitled?node-id=0-1&p=f&t=tUYbPMr0aRaBth2O-0