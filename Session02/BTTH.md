Nhiệm vụ 1: Phân tích bối cảnh và Khái niệm Hệ thống thông tin FastMart

1. Nhận diện 5 thành phần cốt lõi của HTTT FastMart-Online
- Phần cứng: Máy chủ, máy tính tại các chi nhánh, máy POS, điện thoại của khách hàng và shipper, thiết bị mạng.
- Phần mềm: Ứng dụng Mobile, Website bán hàng, hệ thống Back-office, hệ thống BI, CSDL.
- Dữ liệu: Thông tin khách hàng, sản phẩm, tồn kho, đơn hàng, shipper, doanh thu, lịch sử mua hàng.
- Quy trình: Khách chọn sản phẩm  Thêm vào giỏ hàng  Xác nhận đơn  Kiểm tra tồn kho  Thanh toán  Chuẩn bị hàng  Điều phối shipper  Giao hàng  Hoàn thành đơn.
- Con người: Khách hàng, Nhân viên bán hàng, Nhân viên kho, Shipper, Quản lý chi nhánh, Giám đốc, Nhân viên IT, Nhân viên phát triển và triển khai phần mềm.

2. Phân loại và mô tả vai trò các phân hệ HTTT
- TPS – Transaction Processing System: Tạo đơn hàng, Thanh toán, Xuất/Nhập kho, Cập nhật tồn kho, Giao hàng.
- MIS – Management Information System: Doanh thu theo ngày, Số lượng đơn hàng, Tồn kho từng chi nhánh, Số đơn giao thành công, Hiệu suất giao hàng.
- DSS – Decision Support System: Sản phẩm bán chạy, Hành vi khách hàng, Nhu cầu tồn kho, Hiệu quả giao hàng.
- EIS – Executive Information System: Doanh thu theo tháng/năm, Tốc độ tăng trưởng, Lợi nhuận, Số lượng khách hàng, Xu hướng kinh doanh.

Nhiệm vụ 2: Đề xuất Quy trình SDLC và Mô hình phát triển phần mềm

1. Trình bày khung quy trình SDLC 7 bước chi tiết cho dự án FastMart-Online
- Bước 1 – Planning: Xác định mục tiêu, phạm vi, ngân sách, thời gian, rủi ro
- Bước 2 – Requirements Analysis: Thu thập và phân tích yêu cầu của khách hàng, nhân viên kho, quản lý.
- Bước 3 – System Design: Thiết kế kiến trúc hệ thống, database, API, giao diện, phân quyền, luồng xử lý.
- Bước 4 – Development: Dev tiến hành lập trình Frontend, Backend, Database, API, tích hợp thanh toán và giao hàng.
- Bước 5 – Testing: Functional Testing, Integration Testing, Performance Testing, Security Testing, User Acceptance Testing.
- Bước 6 – Deployment: Đưa hệ thống vào sử dụng.
- Bước 7 – Maintenance: Bảo trì sau khi triển khai, cập nhật tính năng, tối ưu hiệu năng, bảo mật, sao lưu dữ liệu, hỗ trợ người dùng

2. Lựa chọn mô hình phát triển phần mềm phù hợp cho hệ thống này và giải thích lý do
- Chọn mô hình Agile/Scrum vì thương mại điện tử có nhiều yêu cầu thay đổi như phương thức thanh toán, chính sách giao hàng, chương trình khuyến mãi, phí vận chuyển, nhận được phản hồi sớm sau mỗi Sprint, giảm rủi ro khi phát hiện lỗi sớm.

Nhiệm vụ 3: Định hình vai trò của UML và Xây dựng Mô hình hóa Hệ thống

1. Giải thích vai trò của UML trong việc xóa bỏ rào cản ngôn ngữ giữa BA, Dev và Tester
- UML – Unified Modeling Language: Ngôn ngữ mô hình hóa dùng để mô tả và thiết kế hệ thống, giúp BA mô tả yêu cầu, Dev hiểu hệ thống cần xây dựng những gì, Tester xác định các chức năng cần kiểm thử.

2. Đề xuất 4 sơ đồ UML phù hợp cho quá trình phân tích và thiết kế hệ thống này và mô tả mục đích sử dụng của từng sơ đồ
- Use Case Diagram  
Mục đích: Xác định ai sử dụng hệ thống và họ làm gì.
+ Customer: Đăng nhập, Xem sản phẩm, Đặt hàng, Thanh toán, Theo dõi đơn
+ Warehouse Staff: Xem tồn kho, Cập nhật tồn kho
+ Shipper: Nhận đơn, Cập nhật trạng thái giao hàng
+ Manager: Xem doanh thu, Xem tồn kho, Xem báo cáo

- Activity Diagram  
Mục đích: Mô tả quy trình nghiệp vụ.

- Class Diagram  
Mục đích: Mô tả cấu trúc dữ liệu và mối quan hệ giữa các đối tượng, giúp Dev thiết kế database và cấu trúc chương trình.
Các class chính: Customer, Product, Order, OrderItem, Payment, Inventory, Branch, Shipper, Delivery

- Sequence Diagram  
Mục đích: Mô tả thứ tự tương tác giữa các đối tượng theo thời gian, giúp Dev hiểu chính xác hệ thống nào gọi hệ thống nào và theo thứ tự nào.