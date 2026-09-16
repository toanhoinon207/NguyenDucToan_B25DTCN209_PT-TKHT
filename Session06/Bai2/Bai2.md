# PHẦN A — Activity Diagram

## Bước 2: Bảng phân rã Node — Swimlane

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
|---|---|---|
| **Initial Node** | Bắt đầu | — |
| **Action** | Đặt đơn hàng | Khách hàng |
| **Decision** | Kiểm tra tồn kho (Còn hàng/Hết hàng) | Bộ phận Kho |
| **Fork** | Đóng gói đơn hàng và Gửi thông báo xuất kho | Bộ phận Kho |
| **Action** | Đóng gói đơn hàng | Bộ phận Kho |
| **Action** | Gửi thông báo xuất kho | Bộ phận Kho |
| **Join** | Gộp 2 nhánh song song | Bộ phận Kho |
| **Final Node** | Kết thúc | — |

## Bước 3: Vẽ Activity Diagram

# PHẦN B — USE CASE DIAGRAM

## Bước 5: Bảng quan hệ

| Use Case A | Use Case B | Quan hệ | Giải thích logic |
|---|---|---|---|
| **Đặt đơn hàng** | **Đăng nhập** | **include** | Khách hàng bắt buộc phải đăng nhập trước khi thực hiện đặt đơn hàng. |
| **Đặt đơn hàng** | **Giao hàng hoả tốc** | **extend** | Giao hàng hoả tốc là chức năng tùy chọn, chỉ được thực hiện khi khách hàng có nhu cầu khi đặt đơn. |
| **Đặt đơn hàng** | **Đặt đơn hàng lẻ** | **generalization** | Đặt đơn hàng lẻ là một dạng chuyên biệt của Đặt đơn hàng. |
| **Đặt đơn hàng** | **Đặt đơn hàng sỉ** | **generalization** | Đặt đơn hàng sỉ là một dạng chuyên biệt của Đặt đơn hàng, dành cho số lượng lớn. |

## Bước 3: Vẽ Use Case Diagram