# PHẦN A — Activity Diagram

## Bước 2: Bảng phân rã Node — Swimlane

| Loại Node | Tên Node / Tác vụ | Swimlane phụ trách |
|---|---|---|
| **Initial Node** | Bắt đầu | — |
| **Action** | Đặt lịch khám | Bệnh nhân |
| **Decision** | Kiểm tra khung giờ (Còn trống / Hết chỗ) | Lễ tân |
| **Fork** | Xác nhận lịch khám và Gửi SMS nhắc lịch | Lễ tân |
| **Action** | Xác nhận lịch khám | Lễ tân |
| **Action** | Gửi SMS nhắc lịch | Lễ tân |
| **Join** | Gộp 2 nhánh song song | Lễ tân |
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