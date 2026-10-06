# Phần 1 - Thiết kế Wifeframe màn hình "Đặt hàng"

## 1. Bảng ánh xạ Use Case -> UI 

| Bước Use Case | Nội dung | UI Element tương ứng	| Mục đích |
|:---:|---|---|---|
| 1 | Khách hàng xem danh sách sản phẩm | Product List | Hiển thị các sản phẩm có thể đặt |
| 2 | Khách hàng chọn 1 sản phẩm và nhập số lượng | Product Item + Quantity Input | Chọn sản phẩm và nhập số lượng |
| 3 | Khách hàng xác nhận đặt hàng | Button | Gửi yêu cầu đặt hàng |
| 4	| Hệ thống kiểm tra số lượng hợp lệ và tạo đơn | Validation Message / Feedback Area	| Hiển thị lỗi nếu số lượng rỗng hoặc ≤ 0 |
| 5 | Hệ thống hiển thị thông báo đặt hàng thành công | Success Message / Feedback Area	| Thông báo kết quả ngay sau khi xác nhận |

## 2. Vẽ Wireframe

https://www.figma.com/design/oHTIgZU6ylrukKgKCcw91N/Session19_Miniproject?node-id=0-1&p=f&t=WSer7esmNtJ1qdV9-0

# Phần 2 - Thiết kế ERD đạt chuẩn 3NF

## 1. Xác định Entity/Attribute/Khóa chính

### Bảng `PRODUCT`

| Attribute | Kiểu dữ liệu | Khóa |
|---|---|---|
| productId | String | PK |
| productName | String |  |
| unitPrice | Double |  |

### Bảng `ORDER`

| Attribute | Kiểu dữ liệu | Khóa |
|---|---|---|
| orderId | String | PK |
| customerName | String |  |
| status | String |  |

# Phần 3 - Rà soát và sửa lỗi chuẩn 

## 1. Bảng dữ liệu nháp đang bị lỗi

| orderId | customerName | productName1 | productName2 | quantity | status |
|---|---|---|---|---:|---|
| ORD-01 | Nguyễn Văn A | Áo thun | Quần jean | 3 | Chờ xử lý |
| ORD-02 | Trần Thị B | Mũ lưỡi trai | *(rỗng)* | 1 | Đã xác nhận |

- Bảng nháp đang vi phạm dạng chuẩn 1NF vì `productName1`, `productName2` là các thuộc tính lặp nhóm dùng để lưu nhiều sản phẩm

## 2. Cách khắc phục

- Tách thành bảng trung gian `ORDER_DETAIL`

### Bảng `ORDER`

| **orderId** | **customerName** | **status** |
|---|---|---|
| ORD-01 | Nguyễn Văn A | Chờ xử lý |
| ORD-02 | Trần Thị B | Đã xác nhận |

### Bảng `PRODUCT`

| productId | productName | unitPrice |
|---|---|---|
| PRD-01 | Áo thun | 150000 |
| PRD-02 | Quần jean | 300000 |
| PRD-03 | Mũ lưỡi trai | 80000 |

### Bảng `ORDER_DETAIL`

| orderId | productId | quantity |
|---|---|---|
| ORD-01 | PRD-01 | 3 |
| ORD-01 | PRD-02 | 2 |
| ORD-02 | PRD-03 | 1 |

# Phần 4 - Viết lại yêu cầu đạt chuẩn Verifiable

- **REQ-01:** Hệ thống phải hiển thị danh sách sản phẩm và hiển thị thông báo kết quả đặt hàng trong thời gian không quá 2 giây kể từ khi khách hàng xác nhận đặt hàng.

# Phần 5 - Đóng gói SRS

# ĐẶC TẢ YÊU CẦU PHẦN MỀM (SRS)

## Hệ thống Đặt hàng nhanh RikkeiMart-Lite

# 1. Introduction

## 1.1 Purpose

Tài liệu mô tả các yêu cầu của phân hệ **Đặt hàng** thuộc hệ thống RikkeiMart-Lite, bao gồm chức năng đặt hàng, giao diện đặt hàng, yêu cầu chức năng và yêu cầu cơ sở dữ liệu.

## 1.2 Scope

Phân hệ cho phép khách hàng:

- Xem danh sách sản phẩm.
- Chọn sản phẩm và nhập số lượng.
- Xác nhận đặt hàng.
- Nhận thông báo kết quả đặt hàng.

Nhân viên xử lý đơn có thể xem các đơn hàng mới trong hàng đợi xử lý và xác nhận đơn hàng.

## 1.3 Definitions and Acronyms

| Thuật ngữ | Ý nghĩa |
|---|---|
| SRS | Software Requirements Specification |
| PK | Primary Key – Khóa chính |
| FK | Foreign Key – Khóa ngoại |
| ERD | Entity Relationship Diagram |
| UC | Use Case – Ca sử dụng |

# 2. Overall Description

## 2.1 Product Perspective

Phân hệ Đặt hàng là một bộ phận của hệ thống RikkeiMart-Lite. Phân hệ sử dụng dữ liệu sản phẩm và đơn hàng để xử lý yêu cầu đặt hàng của khách hàng.

## 2.2 Product Functions

### Use Case: Đặt hàng

**Actor chính:** Khách hàng  
**Actor phụ:** Nhân viên xử lý đơn

**Preconditions:**

- Khách hàng đang ở màn hình danh sách sản phẩm.
- Kho có ít nhất một sản phẩm được hiển thị.

**Main Flow:**

1. Khách hàng xem danh sách sản phẩm.
2. Khách hàng chọn sản phẩm và nhập số lượng.
3. Khách hàng xác nhận đặt hàng.
4. Hệ thống kiểm tra số lượng và tạo đơn hàng với trạng thái **“Chờ xử lý”**.
5. Hệ thống hiển thị thông báo đặt hàng thành công.

**Exception Flow:**

- 4a. Nếu số lượng rỗng hoặc nhỏ hơn hoặc bằng 0, hệ thống hiển thị thông báo lỗi và không tạo đơn hàng.

**Postcondition:**

- Đơn hàng mới xuất hiện trong hàng đợi xử lý để nhân viên xử lý đơn xem và xác nhận.

## 2.3 User Characteristics

| Người dùng | Đặc điểm |
|---|---|
| Khách hàng | Xem sản phẩm, chọn sản phẩm, nhập số lượng và đặt hàng |
| Nhân viên xử lý đơn | Xem và xác nhận các đơn hàng đang chờ xử lý |

## 2.4 Constraints

- Đơn hàng mới phải có trạng thái **“Chờ xử lý”**.
- Chỉ nhân viên xử lý đơn mới xác nhận đơn hàng.
- Số lượng sản phẩm phải lớn hơn 0.
- Một đơn hàng có thể chứa một hoặc nhiều sản phẩm.

## 2.5 User Interface

Màn hình Đặt hàng phải gồm:

- Danh sách sản phẩm.
- Thông tin sản phẩm.
- Ô nhập số lượng.
- Nút **“Xác nhận đặt hàng”**.
- Khu vực hiển thị kết quả đặt hàng.

Sau khi khách hàng xác nhận, hệ thống phải hiển thị ngay một trong hai trạng thái:

- **Thành công:** hiển thị thông báo đặt hàng thành công.
- **Lỗi:** hiển thị thông báo lỗi khi số lượng không hợp lệ.

# 3. Specific Requirements

## 3.1 Functional Requirements

### REQ-01 — Hiển thị và phản hồi đặt hàng

Hệ thống phải hiển thị danh sách sản phẩm và hiển thị thông báo kết quả đặt hàng **trong thời gian không quá 2 giây** kể từ khi khách hàng xác nhận đặt hàng.

## 3.2 Business Rules

- Một khách hàng có thể tạo nhiều đơn hàng.
- Mỗi đơn hàng được tạo bởi đúng một khách hàng.
- Đơn hàng mới luôn có trạng thái **“Chờ xử lý”**.
- Trạng thái chỉ chuyển sang **“Đã xác nhận”** sau khi nhân viên xử lý đơn xác nhận.
- Mỗi đơn hàng có thể chứa một hoặc nhiều sản phẩm.
- Số lượng sản phẩm phải lớn hơn 0.

## 3.3 Product Requirements

### Thông tin sản phẩm

| Thuộc tính | Kiểu dữ liệu | Ràng buộc |
|---|---|---|
| productId | String | PK, duy nhất, tự sinh |
| productName | String | Bắt buộc, không rỗng |
| unitPrice | Double | Bắt buộc, > 0 |

## 3.4 Database Requirements

### Entity PRODUCT

| Thuộc tính | Khóa | Mô tả |
|---|---|---|
| productId | PK | Mã sản phẩm |
| productName | | Tên sản phẩm |
| unitPrice | | Đơn giá |

### Entity ORDER

| Thuộc tính | Khóa | Mô tả |
|---|---|---|
| orderId | PK | Mã đơn hàng |
| customerName | | Tên khách hàng |
| status | | Trạng thái đơn hàng |

### Entity ORDER_DETAIL

| Thuộc tính | Khóa | Mô tả |
|---|---|---|
| orderId | PK, FK | Mã đơn hàng |
| productId | PK, FK | Mã sản phẩm |
| quantity | | Số lượng sản phẩm |

**Quan hệ:**

ORDER 1 ----- N ORDER_DETAIL N ----- 1 PRODUCT