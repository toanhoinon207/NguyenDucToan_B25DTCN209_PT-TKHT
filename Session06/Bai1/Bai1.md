# PHẦN A — Activity Diagram

## Bước 2: Bảng phân rã Node — Swimlane

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
|---|---|---|
| **Initial Node** | Bắt đầu | — |
| **Action** | Quét mã QR | Khách hàng |
| **Decision** | Kiểm tra số dư (Đủ / Không đủ) | Hệ thống |
| **Fork** | Nhả tiền và Gửi SMS | Hệ thống |
| **Action** | Nhả tiền | Hệ thống |
| **Action** | Gửi SMS báo biến động số dư | Hệ thống |
| **Join** | Gộp 2 nhánh song song | Hệ thống |
| **Final Node** | Kết thúc | — |

## Bước 3: Vẽ Activity Diagram

# PHẦN B — USE CASE DIAGRAM

## Bước 5: Bảng quan hệ

| Use Case A | Use Case B | Quan hệ | Giải thích logic |
|---|---|---|---|
| **Rút tiền** | **Đăng nhập** | **include** | Phải đăng nhập (quét mã QR) trước khi thực hiện rút tiền. Đây là chức năng **bắt buộc**. |
| **Rút tiền** | **In hóa đơn giao dịch** | **extend** | In hóa đơn là chức năng **tùy chọn**, chỉ thực hiện khi khách hàng có nhu cầu sau khi rút tiền. |
| **Rút tiền** | **Rút tiền tiêu chuẩn** | **generalization** | Rút tiền tiêu chuẩn là một dạng chuyên biệt của Rút tiền. |
| **Rút tiền** | **Rút tiền nhanh** | **generalization** | Rút tiền nhanh là một dạng chuyên biệt của Rút tiền, cho phép rút nhanh mà không cần chọn mệnh giá. |

## Bước 3: Vẽ Use Case Diagram