# Bước 1 — Tự lập bảng lỗi phát hiện được

| STT | Nội dung lỗi | Phân loại lỗi (Sai vị trí IEEE 830 / Vi phạm đặc tính vàng nào) | Vị trí đúng hoặc cách khắc phục |
|---|---|---|---|
| 1 | Actor chính và Use Case đang đặt tại 2.4 Constraints | Sai vị trí IEEE 830 | Use Case -> 2.2 Product Functions; thông tin về nhóm người dùng/Actor -> 2.3 User Characteristics |
| 2 | Sơ đồ ERD đang đặt trong 1.3 Definitions | Sai vị trí IEEE 830 | Chuyển sang 3.4 Database Requirements |
| 3 | REQ-21: “phản hồi báo giá ... **nhanh chóng**” | Verifiable | Thay “nhanh chóng” bằng thời gian cụ thể, ví dụ không quá 30 giây |
| 4 | REQ-22: “xác nhận thanh toán đủ 100%” nhưng chưa nói rõ hệ thống dựa trên kết quả thanh toán nào để chuyển trạng thái | Complete | Quy định rõ chỉ chuyển Đã xác nhận khi hệ thống nhận được kết quả thanh toán thành công và số tiền đã thanh toán = 100% giá trị hợp đồng |
| 5 | REQ-24 cấm mọi chỉnh sửa báo giá sau khi thanh toán | Consistent | Thống nhất với quy tắc mới: sau khi thanh toán đủ 100%, báo giá bị khóa |

# Bước 2 — Đề xuất bản chỉnh sửa hoàn chỉnh

## 1. Viết lại toàn bộ các mục bị sai vị trí vào đúng chương/mục IEEE 830

| Nội dung | Vị trí đúng |
|---|---|
| Phạm vi hệ thống | 1.2 Scope |
| Định nghĩa thuật ngữ | 1.3 Definitions |
| Use Case / chức năng | 2.2 Product Functions |
| Actor / đặc điểm người dùng | 2.3 User Characteristics |
| Ràng buộc | 2.4 Constraints |
| REQ-21 → REQ-25 | 3.2 Functional Requirements |
| ERD | 3.4 Logical Database Requirements |

## 2. Viết lại REQ-21 đạt chuẩn Verifiable

REQ-21: Sau khi nhận được yêu cầu đặt tour hợp lệ, hệ thống phải phản hồi báo giá cho khách hàng doanh nghiệp trong thời gian không quá 30 giây.

## 3. Xử lý dứt điểm mâu thuẫn giữa REQ-23 và REQ-24, đề xuất 1 quy tắc nghiệp vụ duy nhất, quán triệt thống nhất toàn tài liệu

Hai yêu cầu mâu thuẫn nhau, vi phạm Consistent.

**Quy tắc nghiệp vụ thống nhất:**

Sau khi hệ thống xác nhận khách hàng đã thanh toán đủ 100% giá trị hợp đồng, báo giá phải được khóa và không được phép chỉnh sửa.

**REQ-23:** Điều phối viên được phép chỉnh sửa báo giá trước thời điểm hệ thống xác nhận khách hàng đã thanh toán đủ 100% giá trị hợp đồng.

**REQ-24:** Sau khi hệ thống xác nhận khách hàng đã thanh toán đủ 100% giá trị hợp đồng, hệ thống phải khóa báo giá và không cho phép bất kỳ người dùng nào chỉnh sửa thông tin báo giá.