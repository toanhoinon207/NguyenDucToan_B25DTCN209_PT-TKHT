# 1. Xác định 2 lỗi

## Lỗi 1: Bước 2

**Thực tập sinh vẽ:**

Cổng Thanh Toán tự kiểm tra định dạng thẻ → **Async** sang một Lifeline khác.

- Cổng Thanh Toán tự kiểm tra trên chính nó, nên phải dùng **Self message**:

- Không được tạo thêm Lifeline để xử lý vì đề đã nói rõ đây là **xử lý nội bộ của Cổng Thanh Toán**.

- Nếu tạo thêm đối tượng không có trong nghiệp vụ, sơ đồ sẽ làm sai mô hình hệ thống và thể hiện một thành phần không thực sự tham gia vào luồng.

## Lỗi 2: Bước 6

**Thực tập sinh vẽ:**

Cổng Thanh Toán -> EmailServer: sendReceiptEmail — **Sync**, rồi chờ Return.

- Không được chờ EmailServer phản hồi mới đi tiếp.

- Nếu dùng Sync, Cổng Thanh Toán phải chờ EmailServer xử lý xong. Khi EmailServer phản hồi chậm, luồng thanh toán cũng bị giữ lại, làm tăng thời gian xử lý.

# 2. Sửa sơ đồ