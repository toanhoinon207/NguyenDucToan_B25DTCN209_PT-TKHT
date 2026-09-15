# Phần 1 – Định nghĩa nghiệp vụ

## 1. Ba quy tắc nghiệp vụ cốt lõi

| Quy tắc nghiệp vụ | Mô tả |
|---|---|
| **Thời hạn đổi trả** | Khách hàng chỉ được tạo yêu cầu đổi trả trong vòng **7 ngày kể từ ngày nhận hàng**. |
| **Bằng chứng đổi trả** | Khách hàng phải cung cấp **hình ảnh hoặc video sản phẩm bị lỗi/không đúng mô tả** khi tạo yêu cầu đổi trả. |
| **Kiểm định hàng trả** | Nhân viên kiểm định kho phải kiểm tra sản phẩm sau khi nhận hàng. Chỉ khi sản phẩm được xác nhận hợp lệ thì hệ thống mới thực hiện hoàn tiền cho khách hàng. |

## 2. Edge Case

### EC-01 – Hàng trả về bị tráo đổi

Khách hàng gửi sản phẩm về kho nhưng nhân viên kiểm định phát hiện sản phẩm thực tế **không đúng với sản phẩm đã được RikkeiShop giao**.

- Hệ thống đánh dấu yêu cầu đổi trả là **Không hợp lệ**.
- Hệ thống không thực hiện hoàn tiền.
- Nhân viên kiểm định ghi nhận lý do từ chối.
- Yêu cầu đổi trả kết thúc.

# Phần 2 – Use Case Diagram Tổng thể

## 1. Xác định Actor

### Primary Actor

| **Actor** | **Vai trò** |
|---|---|
| **Khách hàng** | Tạo yêu cầu đổi trả và theo dõi kết quả |
| **Nhân viên kiểm định kho** | Kiểm tra sản phẩm được gửi trả |

### Secondary Actor

| **Actor** | **Vai trò** |
|---|---|
| **Shipper** | Thu hồi sản phẩm từ Khách hàng và giao về kho |
| **Cổng thanh toán** | Thực hiện giao dịch hoàn tiền cho Khách hàng |

## 2. Danh sách Use Case

| Mã | Use Case |
|---|---|
| **UC-01** | Tạo yêu cầu đổi trả |
| **UC-02** | Kiểm tra điều kiện đổi trả |
| **UC-03** | Gửi bằng chứng sản phẩm |
| **UC-04** | Thu hồi sản phẩm |
| **UC-05** | Kiểm định sản phẩm trả |
| **UC-06** | Hoàn tiền đơn hàng |
| **UC-07** | Theo dõi yêu cầu đổi trả |

## 3. Quan hệ Include / Extend

- **[Tạo yêu cầu đổi trả]** **`<<include>>`** **[Kiểm tra điều kiện đổi trả]**
- **[Tạo yêu cầu đổi trả]** **`<<include>>`** **[Gửi bằng chứng sản phẩm]**
- **[Kiểm định sản phẩm trả]** **`<<include>>`** **[Hoàn tiền đơn hàng]**
- **[Thu hồi sản phẩm]** **`<<extend>>`** **[Tạo yêu cầu đổi trả]**
- **[Theo dõi yêu cầu đổi trả]** được thực hiện độc lập bởi Khách hàng.

## 4. Use Case Diagram

https://drive.google.com/file/d/1VqRLn6Vs9zgjh59TkoqTxQJtmH669J9g/view?usp=drive_link

# Phần 3 – Use Case Specification

## UC-01 – Tạo yêu cầu đổi trả

### 1. Tên & ID Use Case

| Thuộc tính | Nội dung |
|---|---|
| **ID** | UC-01 |
| **Tên Use Case** | Tạo yêu cầu đổi trả |

### 2. Actor(s) & Mô tả

| Thành phần | Nội dung |
|---|---|
| **Actor chính** | Khách hàng |
| **Actor phụ** | Shipper |
| **Mô tả** | Cho phép Khách hàng tạo yêu cầu đổi trả đối với sản phẩm bị lỗi hoặc không đúng mô tả. Hệ thống kiểm tra điều kiện và tiếp nhận yêu cầu để thực hiện quy trình thu hồi, kiểm định và hoàn tiền. |

### 3. Pre-conditions

- Khách hàng đã đăng nhập vào tài khoản RikkeiShop.
- Đơn hàng đã được giao thành công.
- Đơn hàng vẫn còn trong thời hạn **7 ngày kể từ ngày nhận hàng**.

### 4. Post-conditions

**Nếu yêu cầu hợp lệ:**

- Yêu cầu đổi trả được tạo thành công.
- Hệ thống lưu thông tin và bằng chứng đổi trả.
- Yêu cầu được chuyển sang bước thu hồi sản phẩm.

**Nếu phát hiện Edge Case:**

- Yêu cầu được đánh dấu **Không hợp lệ**.
- Hệ thống không thực hiện hoàn tiền.

### 5. Main Flow

| **Bước** | **Actor** | **Hành động** |
|:---:|---|---|
| **1** | Khách hàng | Chọn đơn hàng và chọn chức năng **[Tạo yêu cầu đổi trả]**. |
| **2** | Hệ thống | Kiểm tra điều kiện đổi trả và xác nhận đơn hàng còn trong thời hạn 7 ngày. |
| **3** | Khách hàng | Nhập lý do đổi trả và gửi hình ảnh/video làm bằng chứng. |
| **4** | Hệ thống | Tạo yêu cầu đổi trả và thông báo cho Shipper thực hiện thu hồi sản phẩm. |
| **5** | Shipper | Thu hồi sản phẩm từ Khách hàng và chuyển sản phẩm về kho để kiểm định. |

### 6. Alternative Flow

#### A1 – Hàng trả về bị tráo đổi

| **Bước** | **Actor** | **Hành động** |
|:---:|---|---|
| **A1.1** | Nhân viên kiểm định kho | Kiểm tra sản phẩm được Shipper chuyển về và phát hiện sản phẩm không đúng với sản phẩm RikkeiShop đã giao. |
| **A1.2** | Hệ thống | Đánh dấu yêu cầu đổi trả là **Không hợp lệ** và ghi nhận lý do từ chối. |
| **A1.3** | Hệ thống | Không thực hiện hoàn tiền và kết thúc yêu cầu đổi trả. |