# Phần I: Phân tích Bối cảnh, Kiến trúc 3-Tier & Xác định Yêu cầu

## 1. Phân tích Kiến trúc 3 tầng (3-Tier Architecture)

### 1.1 Presentation Layer

| Thành phần | Nhiệm vụ |
|---|---|
| Web Browser | Cho phép khách hàng tìm kiếm sản phẩm, quản lý giỏ hàng, đặt hàng và thanh toán |
| Mobile App | Cung cấp các chức năng mua hàng trên thiết bị di động |
| POS Terminal | Hỗ trợ thu ngân tạo đơn hàng và thanh toán tại siêu thị |

### 1.2. Business Logic Layer

| Thành phần | Nhiệm vụ |
|---|---|
| Order API | Tạo, cập nhật và xác nhận đơn hàng |
| Inventory Service | Kiểm tra và khóa/trừ tồn kho |
| Promotion Service | Kiểm tra và áp dụng Voucher/khuyến mãi |
| Payment Service | Xử lý thanh toán và trạng thái giao dịch |
| Authentication Service | Xác thực người dùng và phân quyền |
| Validation | Kiểm tra dữ liệu đầu vào trước khi xử lý |

### 1.3. Data Access Layer

| Thành phần | Nhiệm vụ |
|---|---|
| Repository / DAO | thực hiện truy vấn dữ liệu |
| MySQL Master | Xử lý các thao tác ghi dữ liệu |
| MySQL Slave | Hỗ trợ các thao tác đọc nhằm giảm tải cho Master |
| Caching | Lưu tạm các dữ liệu thường xuyên được truy cập như thông tin sản phẩm |
| Transaction & Lock | Đảm bảo tính nhất quán khi cập nhật tồn kho và đơn hàng |

### 1.4. Ba lý do kiến trúc 3-Tier khắc phục hệ thống cũ

**Lý do 1 - Giảm nghẽn hệ thống**

- Presentation chỉ gửi request.
- Business Layer xử lý nghiệp vụ.
- Data Access Layer quản lý truy cập dữ liệu.
- Có thể mở rộng từng tầng khi tải tăng.

-> Giúp hệ thống dễ mở rộng và giảm nguy cơ nghẽn khi lượng truy cập tăng cao.

**Lý do 2 - Bảo vệ CSDL**

- Web, Mobile App và POS không được truy cập trực tiếp MySQL.

-> CSDL được tách khỏi tầng giao diện, giảm nguy cơ lộ thông tin truy cập và truy cập trái phép vào CSDL.

**Lý do 3 - Dễ bảo trì và mở rộng**

- Các chức năng được phân tách thành các tầng độc lập:

- Thay đổi giao diện Mobile không cần thay đổi CSDL.
- Thay đổi cách lưu dữ liệu không cần thay đổi giao diện.
- Có thể mở rộng Inventory Service hoặc Payment Service khi lượng giao dịch tăng.

-> Giúp hệ thống dễ bảo trì, kiểm thử và mở rộng hơn Monolithic.

## 2. Thu thập yêu cầu & Stakeholders Matrix

### 2.1. Ma trận nhu cầu tra cứu Hồ sơ SRS
| Stakeholder | Nhu cầu tra cứu trong SRS | Mục đích sử dụng |
|---|---|---|
| Ban Giám đốc FastMart	| Phạm vi hệ thống, mục tiêu, FR/NFR, SLA, bảo mật, tiêu chí nghiệm thu | Xác định hệ thống có đáp ứng mục tiêu kinh doanh hay không |
| PM Dự án | Phạm vi, yêu cầu, Use Case, tiến độ, ràng buộc, Change Log | Quản lý phạm vi và kiểm soát thay đổi |
| Đội Backend/Frontend | FR, NFR, Use Case, API, Business Rules, Database Requirements, UI | Làm căn cứ để thiết kế và lập trình |
| QA/Tester | FR, NFR, Use Case, Alternative Flow, Exception Flow, Business Rules | Xây dựng Test Case và kiểm thử hệ thống

### 2.2. User Story - Khách hàng

**UC-001:** Là một Khách hàng, tôi muốn tìm kiếm sản phẩm, thêm sản phẩm vào giỏ hàng và thanh toán trực tuyến để có thể đặt hàng nhanh chóng trên Web/Mobile App.

### 2.3 User Story - Thu ngân POS

**UC-002:** Là một Thu ngân POS, tôi muốn tạo đơn hàng và thực hiện thanh toán tại quầy để có thể hoàn tất giao dịch cho khách hàng tại siêu thị.

### 2.4. User Story - Quản lý Kho

**UC-003:** Là một Quản lý Kho, tôi muốn theo dõi và cập nhật tồn kho theo thời gian thực để có thể đảm bảo số lượng hàng hóa chính xác và hạn chế tình trạng bán vượt tồn kho.

### 2.5. Functional Requirements

| ID | Yêu cầu chức năng |
|---|---|
| FR-ORD-001 | Hệ thống phải cho phép khách hàng tạo đơn hàng trực tuyến từ các sản phẩm trong giỏ hàng. |
| FR-INV-001 | Hệ thống phải kiểm tra số lượng tồn kho trước khi xác nhận đơn hàng và thực hiện Hold số lượng hàng tương ứng. |
| FR-PAY-001 | Hệ thống phải cho phép thanh toán bằng CASH, BANK_TRANSFER, VNPAY hoặc MOMO. |
| FR-PRO-001 | Hệ thống phải kiểm tra thời hạn và số lượt sử dụng còn lại của Voucher trước khi áp dụng. |

### 2.6. Non-functional Requirements

| ID | Nhóm | Yêu cầu |
|---|---|---|
| NFR-AVL-001 | SLA / Uptime | Hệ thống phải đạt SLA Uptime tối thiểu 99,9% trong mỗi tháng, không tính thời gian bảo trì được thông báo trước. |
| NFR-PERF-001 | Latency | Hệ thống phải phản hồi yêu cầu checkout trong dưới 2 giây đối với điều kiện tải được quy định. |
| NFR-SEC-001 | Bảo mật | Hệ thống phải sử dụng HTTPS/TLS để mã hóa dữ liệu trao đổi giữa Client và Server, đồng thời bảo vệ dữ liệu nhạy cảm trong quá trình lưu trữ. |
| NFR-SCAL-001 | Khả năng chịu tải | Hệ thống phải hỗ trợ tối thiểu 10.000 người dùng đồng thời (CCU) mà không xảy ra mất dữ liệu hoặc Over-selling do quá tải. |

# Phần II: Mô hình hóa Luồng Nghiệp vụ & Sơ đồ Use Case

## 1. Sơ đồ Activity Diagram với Swimlanes

## 2. Sơ đồ Use Case Diagram & Bảng Đặc tả

### 2.1. Sơ đồ Use Case Diagram

### 2.2. Bảng Đặc tả Use Case chi tiết

| Thành phần | Đặc tả |
|---|---|
| **Use Case ID** | UC-01 |
| **Use Case Name** | Đặt hàng trực tuyến (Place Order) |
| **Primary Actor** | Customer |
| **Pre-conditions** | 1. Customer đã chọn ít nhất một sản phẩm và nhập số lượng.<br>2. Giỏ hàng có sản phẩm hợp lệ.<br>3. Hệ thống đang hoạt động bình thường. |
| **Post-conditions** | **Thành công:** Đơn hàng được tạo với trạng thái **CONFIRMED**, tồn kho được giữ/trừ theo quy định và thông tin thanh toán được cập nhật.<br>**Thất bại:** Đơn hàng không được xác nhận; tồn kho được giải phóng nếu đã Hold Stock. |

#### Main Flow – Luồng chính

| Bước | Actor/System | Thao tác |
|:---:|---|---|
| 1 | Customer | Chọn sản phẩm và nhập số lượng. |
| 2 | Customer | Xác nhận giỏ hàng và chọn **Đặt hàng trực tuyến**. |
| 3 | System | Kiểm tra tính hợp lệ của dữ liệu đơn hàng. |
| 4 | System | Kiểm tra tồn kho của các sản phẩm. |
| 5 | System | Giữ tồn kho (**Hold Stock**) trong 15 phút. |
| 6 | System | Tạo đơn hàng với trạng thái **PENDING**. |
| 7 | System | Chuyển yêu cầu đến Payment Gateway để xử lý thanh toán. |
| 8 | Payment Gateway | Xử lý giao dịch thanh toán. |
| 9 | System | Nhận kết quả thanh toán thành công. |
| 10 | System | Cập nhật đơn hàng sang trạng thái **CONFIRMED**. |
| 11 | System | Hoàn tất đặt hàng. |

#### Alternative Flow – Luồng rẽ nhánh

| Mã | Tại bước | Điều kiện | Xử lý |
|---|:---:|---|---|
| **A1** | 3 | Customer có nhập Voucher | Hệ thống kiểm tra hạn sử dụng và lượt sử dụng của Voucher, sau đó áp dụng Voucher nếu hợp lệ. |
| **A2** | 3 | Không sử dụng Voucher | Hệ thống bỏ qua bước kiểm tra Voucher và tiếp tục kiểm tra tồn kho. |
| **A3** | 9 | Thanh toán **Timeout** | Đơn hàng chuyển sang trạng thái **chờ đối soát**. Sau 5 phút, hệ thống thực hiện **Reconciliation**. Nếu thanh toán thành công → **CONFIRMED**. |
| **A4** | 9 | Reconciliation không thành công | Hệ thống **Release Stock** và không xác nhận đơn hàng. |

#### Exception Flow – Luồng ngoại lệ

| Mã | Tại bước | Ngoại lệ | Xử lý |
|---|---:|---|---|
| **E1** | 3 | Dữ liệu đơn hàng không hợp lệ | Hệ thống trả lỗi **400 Bad Request**, yêu cầu Customer kiểm tra lại dữ liệu. |
| **E2** | 4 | Không đủ tồn kho | Hệ thống từ chối đơn hàng và thông báo sản phẩm không đủ số lượng. |
| **E3** | 3 | Voucher không hợp lệ/hết hạn/hết lượt sử dụng | Hệ thống thông báo lỗi Voucher; đơn hàng không được áp dụng Voucher. |
| **E4** | 9 | Thanh toán thất bại | Đơn hàng chuyển sang **FAILED** và hệ thống giải phóng tồn kho đã giữ. |
| **E5** | 9 | Payment Gateway không phản hồi | Hệ thống giữ đơn ở trạng thái chờ xử lý/đối soát và thực hiện Reconciliation theo quy định. |

# Phần III: Thiết kế Kỹ thuật Chi tiết - Class, Sequence, UI/UX & ERD

## 1. Trích xuất Class Diagram

## 2. Thiết kế Sequence Diagram

## 3. Phác thảo UI/UX Wireframe

https://www.figma.com/design/8U8KvZAXGHQHSrc43BG37x/Session19_Miniproject?node-id=0-1&p=f&t=1HtfLqhB9BpD5HTX-0

## 4. Thiết kế CSDL ERD đạt chuẩn 3NF