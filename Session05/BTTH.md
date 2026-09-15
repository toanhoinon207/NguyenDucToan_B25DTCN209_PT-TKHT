# Nhiệm vụ 1: Phân tích Quy trình nghiệp vụ và Thiết kế Activity Diagram

## 1. Các thành phần của Activity Diagram

| Thành phần | Ý nghĩa |
|---|---|
| **Start Node** | Điểm bắt đầu của quy trình |
| **End Node** | Điểm kết thúc của quy trình |
| **Action Node** |	Biểu diễn một hành động được thực hiện trong quy trình |
| **Decision Node** |	Kiểm tra điều kiện và phân chia luồng xử lý |
| **Fork Node** |	Chia một luồng thành nhiều luồng được thực hiện song song |
| **Join Node** |	Gom các luồng xử lý song song lại |
| **Swimlane** | Phân chia trách nhiệm xử lý cho từng đối tượng |

## 2. Activity Diagram

https://drive.google.com/file/d/1Qwf2Rmwso2IQNLfQR-PnmomrCGRagK2Z/view?usp=drive_link

# Nhiệm vụ 2: Nhận diện Actor và Trích xuất Use Case

## 1. Danh sách Actor

### Actor chính – Primary Actor

| Actor |	Vai trò |
|---|---|
| **Khách hàng** | Tìm kiếm món ăn, đặt đồ ăn và thực hiện thanh toán |
| **Shipper**	| Nhận đơn và thực hiện giao hàng |

### Actor phụ – Secondary Actor

| Actor |	Vai trò |
|---|---|
| **Cổng Momo** | Xử lý giao dịch thanh toán trực tuyến |
| **Máy chủ SMS**	| Gửi tin nhắn xác nhận đơn hàng cho Khách hàng |

## 2. Danh sách Use Case

| STT | Mã Use Case | Tên Use Case |
|:---:|:---:|---|
| **1** | UC-01 | Đặt đồ ăn |
| **2** | UC-02 | Tìm kiếm món ăn |
| **3** | UC-03 | Xác thực tài khoản |
| **4** | UC-04 | Áp mã giảm giá |
| **5** | UC-05 | Thanh toán đơn hàng |
| **6** | UC-06 | Nhận đơn giao hàng |
| **7** | UC-07 | Cập nhật trạng thái giao hàng |
| **8** | UC-08 | Đối soát tiền thu |

# Nhiệm vụ 3: Use Case Specification

## 1. Thông tin chung

| Thuộc tính | Nội dung |
|---|---|
| **Mã Use Case** | UC-01 |
| **Tên Use Case** | Đặt đồ ăn và Thanh toán |
| **Actor chính** | Khách hàng |
| **Actor phụ** | Cổng Momo |

## 2. Mô tả tóm tắt

- Use Case cho phép Khách hàng lựa chọn món ăn, đặt đồ ăn và thanh toán đơn hàng trực tuyến thông qua Cổng Momo.
- Hệ thống kiểm tra tồn kho trước khi thực hiện thanh toán và xử lý các trường hợp hết món hoặc thanh toán thất bại.

## 3. Tiền điều kiện

- Khách hàng đã mở ứng dụng QuickBite.
- Khách hàng đã có tài khoản trên hệ thống.
- Khách hàng đã lựa chọn món ăn muốn đặt.
- Hệ thống QuickBite đang hoạt động.

## 4. Hậu điều kiện

### Nếu thành công:

- Đơn hàng được tạo trên hệ thống.
- Trạng thái thanh toán được ghi nhận thành công.
- Hệ thống gửi SMS xác nhận cho Khách hàng.
- Shipper nhận được thông báo về đơn hàng mới.

### Nếu thất bại:

- Đơn hàng chưa được xác nhận thành công.
- Thanh toán chưa được ghi nhận là thành công.

## 5. Luồng sự kiện chính – Main Flow

| Bước | Actor | Mô tả |
|:---:|---|---|
| **1** | Khách hàng | Mở ứng dụng, tìm kiếm món ăn và nhấn Đặt hàng. |
| **2** | Hệ thống | Xác thực tài khoản, kiểm tra tồn kho và hiển thị tổng tiền. |
| **3** | Khách hàng | Xác nhận đơn hàng và chọn phương thức thanh toán Momo. |
| **4** | Hệ thống | Gửi yêu cầu thanh toán đến Cổng Momo. |
| **5** | Khách hàng | Xác nhận thanh toán trên Momo. |
| **6** | Hệ thống | Nhận kết quả thanh toán thành công, tạo đơn hàng, gửi SMS xác nhận và thông báo đơn hàng mới cho Shipper. |

## 6. Luồng sự kiện thay thế – Alternative Flow

### A1 – Hết món ăn trong kho

| Bước | Mô tả |
|---|---|
| **A1.1** | Tại bước 2, Hệ thống phát hiện món ăn đã hết hàng. |
| **A1.2** | Hệ thống hiển thị thông báo **"Món ăn đã hết"**. |
| **A1.3** | Quy trình kết thúc. |

### A2 – Thanh toán Momo thất bại

| Bước | Mô tả |
|---|---|
| **A2.1** | Tại bước 5, Cổng Momo trả về kết quả thanh toán thất bại. |
| **A2.2** | Hệ thống hiển thị thông báo **"Thanh toán thất bại"**. |
| **A2.3** | Hệ thống cho phép Khách hàng chọn lại phương thức thanh toán. |
| **A2.4** | Khách hàng chọn phương thức thanh toán khác và tiếp tục thực hiện thanh toán. |

# Nhiệm vụ 4: Thiết kế Use Case Diagram chuẩn 3 Vùng

https://drive.google.com/file/d/11NQCkakKmSyYHZGWpq32N31My2s2mEJD/view?usp=drive_link