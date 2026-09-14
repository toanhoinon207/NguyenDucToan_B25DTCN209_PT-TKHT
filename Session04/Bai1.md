# Bước 1: Nhận diện 5 thành phần HTTT và phân biệt Dữ liệu vs Thông tin

## 1. Nhận diện 5 thành phần HTTT

| Thành phần HTTT | Ví dụ thực tế tại phòng khám RikkeiCare | Vai trò cơ bản |
|---|---|---|
| **1. Phần cứng (Hardware)** | Máy tính để bàn tại quầy lễ tân, máy chủ lưu trữ | Thiết bị vật lý để nhập liệu và xử lý |
| **2. Phần mềm (Software)** | Phần mềm quản lý phòng khám RikkeiCare | Ứng dụng hỗ trợ nghiệp vụ khám chữa bệnh |
| **3. Dữ liệu (Data)** | Danh sách bệnh nhân, hồ sơ bệnh án điện tử | Dữ liệu lưu trữ phục vụ chẩn đoán |
| **4. Con người (People)** | Bác sĩ khám bệnh, nhân viên tiếp tân | Người trực tiếp sử dụng và vận hành |
| **5. Quy trình (Process)** | Đăng kí --> Kiểm tra thông tin --> Phát số --> Chờ khám | Các bước tiếp nhận và phục vụ bệnh nhân |

## 2. Phân biệt Dữ liệu và Thông tin

| STT | Nội dung dữ liệu tại phòng khám | Dữ liệu (Data) | Thông tin (Information) | Lý do phân loại |
|---|---|:---:|:---:|---|
| **1** | 38.5 | [x] | [] | Số liệu thô, chưa có đơn vị và ngữ cảnh |
| **2** | Bệnh nhân Nguyễn Văn A, thân nhiệt 38.5 độ C, đo lúc 08:30 sáng | [] | [x] | Đã có ngữ cảnh đầy đủ: Ai, Chỉ số gì, Khi nào |
| **3** | 1500000 | [x] | [] | Chuỗi số thô, chưa có đơn vị tiền tệ hay mục đích |
| **4** | Tổng doanh thu tiền khám bệnh trong ngày là 15.000.000 VNĐ | [] | [x] | Số liệu đã được xử lý và có đơn vị rõ ràng |
| **5** | BN001, Trần Thị B, 45, Nữ | [x] | [] | Dữ liệu thô chưa thể hiện kết luận hay phân tích |

# Bước 2: Khảo sát môi trường và xác định Stakeholders

## 1. Phân loại môi trường

| Yếu tố khảo sát tại phòng khám | Thuộc loại môi trường | Tầm ảnh hưởng đến hệ thống |
|---|---|---|
| **Kỹ năng máy tính của y tá** | **Môi trường Nội bộ** | Giao diện phần mềm cần đơn giản, dễ thao tác |
| **Quy định bảo mật của Bộ Y tế** | **Môi trường Bên ngoài** | Hệ thống bắt buộc phải tuân thủ quy chuẩn pháp lý |
| **Hạ tầng mạng nội bộ phòng khám** | **Môi trường Nội bộ** | Ảnh hưởng đến tốc độ vận hành phần mềm |
| **Ý kiến phản hồi từ bệnh nhân** | **Môi trường Bên ngoài** | Giúp phòng khám phát hiện vấn đề và cải thiện chức năng, giao diện hệ thống |
| **Ứng dụng đặt khám từ đối thủ** | **Môi trường Bên ngoài** | Tạo áp lực cạnh tranh, yêu cầu hệ thống phải cải thiện tính năng và trải nghiệm người dùng |

## 2. Xác định Stakeholders

| Nhóm Stakeholder | Vai trò trong dự án | Mối quan tâm lớn nhất đối với phần mềm |
|---|---|---|
| **1. Bác sĩ khám bệnh** | Người dùng chuyên môn | Tra cứu nhanh lịch sử bệnh án và kê đơn thuốc tiện lợi |
| **2. Bệnh nhân** | Người thụ hưởng dịch vụ | Đặt lịch khám dễ dàng, không phải chờ đợi lâu |
| **3. Nhân viên tiếp tân** | Người tiếp nhận và quản lý thông tin bệnh nhân | Nhập thông tin nhanh, quản lý lịch hẹn và giảm thời gian chờ của bệnh nhân |

# Bước 3: Lựa chọn kỹ thuật thu thập yêu cầu và soạn câu hỏi mẫu

## 1. Lựa chọn kỹ thuật khảo sát

| STT | Tình huống khảo sát thực tế | Kỹ thuật phù hợp nhất | Lý do lựa chọn ngắn gọn |
|:---:|---|---|---|
| **1** | Tìm hiểu mục tiêu chiến lược và ngân sách từ Giám đốc phòng khám | **Phỏng vấn (Interview)** | Số lượng người ít, cần trao đổi sâu và chi tiết |
| **2** | Thu thập ý kiến từ hơn 1.000 bệnh nhân về sự tiện lợi khi đặt lịch hẹn | **Bảng câu hỏi / Khảo sát (Survey)** | Số lượng người dùng lớn, thu thập nhanh số liệu định lượng |
| **3** | Xem thực tế quy trình tiếp đón và phát số thứ tự tại quầy tiếp tân | **Quan sát (Observation)** | (Học viên giải thích) | Có thể trực tiếp theo dõi thao tác và các bước thực tế đang diễn ra |
| **4** | Nắm rõ quy định về biểu mẫu phiếu khám bệnh và danh mục thuốc | **Nghiên cứu tài liệu (Document Analysis)** | Biểu mẫu và quy chế là tài liệu có sẵn, chuẩn pháp lý |
| **5** | Tìm hiểu mong muốn sắp xếp ca trực của đội ngũ 20 y tá | **Phỏng vấn (Interview)** | Số lượng người vừa phải, cần trao đổi trực tiếp để hiểu nhu cầu và khó khăn |

## 2. Câu hỏi phỏng vấn mở dành cho Bác sĩ

Thầy/Cô đang gặp những khó khăn lớn nhất nào khi sử dụng hệ thống hiện tại để tra cứu hồ sơ bệnh án, nhập kết quả khám và kê đơn thuốc cho bệnh nhân?

# Bước 4: Phân loại Yêu cầu Chức năng (FR) và Phi chức năng (NFR)

| STT | Phát biểu yêu cầu | Phân loại (FR / NFR) | Mã định danh đề xuất | Câu hỏi cốt lõi giải thích |
|---|---|---|---|---|
| **(1)** | Bệnh nhân có thể đặt lịch khám theo bác sĩ trên website | **FR** | FR-01 | Đây là hành động/tính năng hệ thống LÀM GÌ |
| **(2)** | Thời gian tải trang hiển thị lịch khám không quá 2 giây | **NFR** | NFR-01 | Tiêu chuẩn hiệu năng: hệ thống chạy TỐT NHƯ THẾ NÀO |
| **(3)** | Mật khẩu tài khoản phải được mã hóa bảo mật khi lưu trữ | **NFR** | NFR-02 | Tiêu chuẩn an toàn: bảo mật TỐT NHƯ THẾ NÀO |
| **(4)** | Bác sĩ có thể nhập kết quả chẩn đoán và kê đơn thuốc điện tử | **FR** | FR-02 | Đây là hành động/tính năng hệ thống LÀM GÌ |
| **(5)** | Hệ thống phải hoạt động liên tục và ổn định 24/7 | **NFR** | NFR-03 | Tiêu chuẩn vận hành: hệ thống vận hành TỐT NHƯ THẾ NÀO |

# Bước 5: Đặc tả User Story chuẩn ba thành phần

## 1. User Story mẫu

"Là một Bệnh nhân, tôi muốn xem lại lịch sử các lần khám bệnh trước đây, để theo dõi tiến triển sức khỏe của bản thân."

## 2. User Story dành cho Bác sĩ

| Thành phần User Story | User Story dành cho Bác sĩ |
|---|---|
| Là một (Vai trò - Who): | Bác sĩ khám bệnh |
| Tôi muốn (Hành động - What): | Xem danh sách bệnh nhân đã đăng ký khám trong ngày |
| Để (Lợi ích - Why): | Nắm được danh sách bệnh nhân và chuẩn bị cho việc khám bệnh, giúp quá trình tiếp nhận và khám diễn ra thuận lợi |