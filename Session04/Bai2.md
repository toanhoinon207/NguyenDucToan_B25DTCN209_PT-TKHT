# Bước 1: Nhận diện 5 thành phần HTTT và phân biệt Dữ liệu vs Thông tin

## 1. Nhận diện 5 thành phần HTTT

| Thành phần HTTT | Ví dụ thực tế tại RikkeiBank | Vai trò cơ bản |
|---|---|---|
| **1. Phần cứng (Hardware)** | Máy chủ xử lý giao dịch Core Banking, máy ATM/POS | Hạ tầng vật lý xử lý và giao tiếp tài chính |
| **2. Phần mềm (Software)** | Ứng dụng RikkeiBank Mobile, hệ thống Internet Banking | Giao diện và logic thực hiện giao dịch số |
| **3. Dữ liệu (Data)** | Số dư tài khoản, lịch sử biến động số dư | Dữ liệu tài chính cốt lõi |
| **4. Con người (People)** | Khách hàng cá nhân, giao dịch viên ngân hàng | Tác nhân trực tiếp tương tác với hệ thống |
| **5. Quy trình (Process)** | Đăng nhập --> Nhập thông tin người nhận --> Xác thực --> Thực hiện giao dịch | Trình tự các bước xác thực và chuyển khoản |

## 2. Phân biệt Dữ liệu và Thông tin

| STT | Nội dung dữ liệu tại RikkeiBank | Dữ liệu (Data) | Thông tin (Information) | Lý do phân loại |
|:---:|---|:---:|:---:|---|
| **1** | 50000000 | [x] | [] | Chuỗi số thô, chưa rõ là tiền gửi, tiền vay hay hạn mức |
| **2** | Khách hàng Trần Văn C chuyển 5.000.000 VNĐ lúc 10:15 ngày 15/08 | [] | [x] | Đầy đủ ngữ cảnh giao dịch: Ai, Số tiền, Thời gian |
| **3** | 0987654321 | [x] | [] | Chuỗi số thô, có thể là số điện thoại hoặc số tài khoản |
| **4** | Tổng số dư tiết kiệm trực tuyến của chi nhánh đạt 200 tỷ VNĐ trong tháng 8 | [] | [x] | Số liệu đã được xử lý và có đơn vị rõ ràng |
| **5** | TK101, Nguyễn Thị D, Active, Gold | [x] | [] | Dữ liệu thô về mã tài khoản, khách hàng, trạng thái và hạng khách hàng |

# Bước 2: Khảo sát môi trường và xác định Stakeholders

## 1. Phân loại môi trường

| Yếu tố khảo sát tại RikkeiBank | Thuộc loại môi trường | Tầm ảnh hưởng đến hệ thống |
|---|---|---|
| **Năng lực bảo mật của đội ngũ IT** | **Môi trường Nội bộ** | Quyết định khả năng phòng chống tấn công mạng |
| **Thông tư an toàn thông tin Ngân hàng Nhà nước** | **Môi trường Bên ngoài** | Quy định bắt buộc về xác thực sinh trắc học |
| **Hệ thống đường truyền liên ngân hàng Napas** | **Môi trường Bên ngoài** | Ảnh hưởng trực tiếp đến tốc độ chuyển tiền liên ngân hàng |
| **Thói quen sử dụng điện thoại của người cao tuổi** | **Môi trường Bên ngoài** | Ảnh hưởng đến cách thiết kế giao diện và thao tác giao dịch trên ứng dụng |
| **Chính sách lãi suất của các ngân hàng đối thủ** | **Môi trường Bên ngoài** | Tạo áp lực cạnh tranh, ảnh hưởng đến nhu cầu phát triển sản phẩm tiết kiệm |

## 2. Xác định Stakeholders

| Nhóm Stakeholder | Vai trò trong dự án | Mối quan tâm lớn nhất đối với phần mềm |
|---|---|---|
| **1. Khách hàng cá nhân** | Người dùng dịch vụ cuối | Chuyển tiền nhanh chóng, an toàn, giao diện mượt mà |
| **2. Chuyên viên An ninh mạng** | Giám sát bảo mật | Hệ thống chống rò rỉ mã OTP và mã hóa dữ liệu đầu cuối |
| **3. Giao dịch viên tại quầy** | Người hỗ trợ và xử lý giao dịch | Tra cứu thông tin nhanh, nhập giao dịch chính xác và hạn chế sai sót |

# Bước 3: Lựa chọn kỹ thuật thu thập yêu cầu và soạn câu hỏi mẫu

## 1. Lựa chọn kỹ thuật khảo sát

| STT | Tình huống khảo sát thực tế | Kỹ thuật phù hợp nhất | Lý do lựa chọn ngắn gọn |
|:---:|---|---|---|
| **1** | Khảo sát nhu cầu giao dịch của 50.000 khách hàng trẻ Gen Z | **Bảng câu hỏi / Khảo sát (Survey)** | Quy mô người dùng cực lớn, thu thập nhanh số liệu định lượng |
| **2** | Làm rõ quy định đối soát và hạn mức chuyển khoản với Giám đốc rủi ro | **Phỏng vấn (Interview)** | Chuyên gia cấp cao, cần trao đổi sâu về chính sách nghiệp vụ |
| **3** | Xem thực tế thao tác nhập lệnh chuyển tiền quốc tế của giao dịch viên | **Quan sát (Observation)** | Có thể trực tiếp theo dõi thao tác và các bước thực tế đang diễn ra |
| **4** | Đọc các văn bản hướng dẫn tiêu chuẩn bảo mật thanh toán PCI-DSS | **Nghiên cứu tài liệu (Document Analysis)** | Tiêu chuẩn quốc tế dạng văn bản quy chuẩn có sẵn |
| **5** | Lấy ý kiến đóng góp của nhóm 15 chuyên viên chăm sóc khách hàng VIP | **Phỏng vấn (Interview)** | Nhóm người dùng có số lượng vừa phải, cần trao đổi trực tiếp để thu thập nhiều ý kiến |

## 2. Câu hỏi trắc nghiệm khảo sát khách hàng cá nhân

Câu hỏi: "Khi chuyển tiền trên ứng dụng RikkeiBank, yếu tố nào quan trọng nhất với bạn?"

A. Tốc độ chuyển tiền

B. Mức độ an toàn và bảo mật

C. Giao diện dễ sử dụng

D. Phí giao dịch thấp

# Bước 4: Phân loại Yêu cầu Chức năng (FR) và Phi chức năng (NFR)

| STT | Phát biểu yêu cầu | Phân loại (FR / NFR) | Mã định danh đề xuất | Câu hỏi cốt lõi giải thích |
|---|---|---|---|---|
| **(1)** | Khách hàng có thể quét mã QR để thanh toán hóa đơn | **FR** | FR-01 | Hành động hệ thống cung cấp (LÀM GÌ) |
| **(2)** | Giao dịch chuyển tiền phải hoàn tất trong vòng dưới 3 giây | **NFR** | NFR-01 | Tiêu chuẩn tốc độ xử lý (TỐT NHƯ THẾ NÀO) |
| **(3)** | Mọi giao dịch trên 10 triệu VNĐ bắt buộc xác thực sinh trắc học khuôn mặt | **NFR** | NFR-02 | Tiêu chuẩn an ninh và bảo mật (TỐT NHƯ THẾ NÀO) |
| **(4)** | Khách hàng có thể mở sổ tiết kiệm trực tuyến ngay trên ứng dụng | **FR** | FR-02 | Đây là chức năng hệ thống cung cấp cho khách hàng |
| **(5)** | Hệ thống Core Banking chịu tải được 10.000 giao dịch đồng thời mỗi giây | **NFR** | NFR-03 | Tiêu chuẩn hiệu năng: khả năng chịu tải TỐT NHƯ THẾ NÀO |

# Bước 5: Đặc tả User Story chuẩn ba thành phần

| Thành phần User Story | User Story dành cho Khách hàng |
|---|---|
| Là một (Vai trò - Who): | Khách hàng sử dụng ứng dụng RikkeiBank |
| Tôi muốn (Hành động - What): | Lưu danh bạ người thụ hưởng thường xuyên chuyển tiền |
| Để (Lợi ích - Why): | Tiết kiệm thời gian nhập thông tin người thụ hưởng và thực hiện chuyển tiền nhanh chóng, thuận tiện |