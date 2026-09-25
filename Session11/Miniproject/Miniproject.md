# Phần I - Phân tích hệ thống và Thu thập yêu cầu

## 1. 5 thành phần HTTT

| Thành phần | DentCare |
|---|---|
| **Phần cứng** | Máy tính tại quầy lễ tân, máy tính của nha sĩ, máy chủ, máy in hóa đơn, thiết bị mạng. |
| **Phần mềm** | Hệ thống quản lý phòng khám DentCare và các phần mềm hỗ trợ. |
| **Dữ liệu** | Thông tin bệnh nhân, lịch hẹn, hồ sơ điều trị, dịch vụ nha khoa, hóa đơn, chi tiết hóa đơn, thanh toán. |
| **Quy trình** | Đặt lịch hẹn, đăng ký bệnh nhân, khám bệnh, ghi hồ sơ điều trị, tạo hóa đơn, thanh toán, báo cáo doanh thu. |
| **Con người** | Bệnh nhân, Lễ tân, Nha sĩ, Quản lý. |

## 2. Phân loại hệ thống thông tin

### DentCare thuộc loại TPS – Transaction Processing System (Hệ thống xử lý giao dịch)

**Lý do**

DentCare xử lý các giao dịch nghiệp vụ hằng ngày như:

- Đặt lịch hẹn.
- Đăng ký bệnh nhân.
- Ghi nhận kết quả khám.
- Tạo hóa đơn.
- Thanh toán.
- Cập nhật hồ sơ bệnh nhân.

## 3. Quy trình SDLC

| Giai đoạn | Công việc | Kết quả đầu ra |
|---|---|---|
| **1. Planning** | Xác định vấn đề của phòng khám, phạm vi và mục tiêu hệ thống. | Kế hoạch dự án, phạm vi dự án |
| **2. Requirement Analysis** | Khảo sát Bệnh nhân, Lễ tân, Nha sĩ, Quản lý; xác định FR/NFR. | SRS, User Story |
| **3. System Design** | Thiết kế Activity, Use Case, Class, Sequence và cơ sở dữ liệu ở mức phân tích. | Các sơ đồ UML, thiết kế hệ thống |
| **4. Implementation** | Lập trình các chức năng của DentCare. | Source Code |
| **5. Testing** | Kiểm thử đặt lịch, khám bệnh, thanh toán, phân quyền và validation. | Test Case, Test Report |
| **6. Deployment** | Triển khai hệ thống cho phòng khám. | Hệ thống DentCare hoạt động |
| **7. Maintenance** | Sửa lỗi, cập nhật chức năng và bảo trì hệ thống. | |

## 4. Mô hình phát triển

**Lựa chọn: Agile.**

Lý do:

- DentCare có nhiều nhóm người dùng với nhu cầu khác nhau.
- Có thể phát triển theo từng chức năng.
- Có thể nhận phản hồi từ Lễ tân, Nha sĩ và Quản lý sau mỗi Sprint.
- Các chức năng có thể được ưu tiên theo mức độ quan trọng.

Có thể chia thành các Sprint:

| Sprint | Nội dung |
|---|---|
| **Sprint 1** | Quản lý bệnh nhân |
| **Sprint 2** | Đặt và quản lý lịch hẹn |
| **Sprint 3** | Khám bệnh và hồ sơ điều trị |
| **Sprint 4** | Hóa đơn và thanh toán |
| **Sprint 5** | Quản lý dịch vụ và báo cáo |

## 5. Stakeholders và thu thập yêu cầu

### Stakeholder

| Stakeholder | Vai trò | Nhu cầu chính |
|---|---|---|
| **Bệnh nhân** | Sử dụng dịch vụ | Đặt lịch, hủy lịch, xem lịch sử khám |
| **Lễ tân** | Vận hành phòng khám | Quản lý bệnh nhân, lịch hẹn, hóa đơn, thanh toán |
| **Nha sĩ** | Khám và điều trị | Xem lịch, khám bệnh, ghi hồ sơ |
| **Quản lý** | Quản lý phòng khám | Quản lý dịch vụ, xem báo cáo |

### Nguồn yêu cầu

| Nguồn | Thông tin thu thập |
|---|---|
| **Con người** | Bệnh nhân, Lễ tân, Nha sĩ, Quản lý |
| **Hệ thống hiện tại** | Sổ lịch hẹn, hồ sơ giấy, hóa đơn viết tay |
| **Tài liệu** | Quy định phòng khám, bảng giá dịch vụ, biểu mẫu hóa đơn |

### Kỹ thuật thu thập

| Stakeholder | Kỹ thuật |
|---|---|
| **Bệnh nhân** | Survey + Interview |
| **Lễ tân** | Observation + Interview |
| **Nha sĩ** | Interview + Observation |
| **Quản lý** | Interview |
| **Hệ thống hiện tại** | Observation + Document Analysis |

## 6. Functional Requirements

| Mã | Yêu cầu chức năng |
|---|---|
| **FR01** | Quản lý thông tin bệnh nhân |
| **FR02** | Đăng ký bệnh nhân |
| **FR03** | Cập nhật hồ sơ bệnh nhân |
| **FR04** | Tra cứu bệnh nhân |
| **FR05** | Đặt lịch hẹn |
| **FR06** | Hủy lịch hẹn |
| **FR07** | Dời lịch hẹn |
| **FR08** | Xem lịch làm việc của nha sĩ |
| **FR09** | Cập nhật lịch làm việc nha sĩ |
| **FR10** | Khám bệnh |
| **FR11** | Ghi nhận MedicalRecord |
| **FR12** | Quản lý dịch vụ nha khoa |
| **FR13** | Tạo hóa đơn |
| **FR14** | Thanh toán |
| **FR15** | Xác nhận thanh toán |
| **FR16** | Xem báo cáo doanh thu |
| **FR17** | Xem số lượt khám |
| **FR18** | Tra cứu lịch sử khám bệnh |

## 7. Non-functional Requirements

| Mã | Yêu cầu phi chức năng |
|---|---|
| **NFR01** | Thời gian phản hồi các thao tác thông thường không quá 3 giây trong điều kiện tải bình thường. |
| **NFR02** | Dữ liệu bệnh nhân phải được bảo vệ và chỉ người có quyền mới được truy cập. |
| **NFR03** | Mỗi tài khoản chỉ được sử dụng các chức năng đúng với quyền được cấp. |
| **NFR04** | Hệ thống phải đảm bảo dữ liệu lịch hẹn không bị trùng. |
| **NFR05** | Dữ liệu lịch sử khám và hóa đơn phải được bảo toàn. |
| **NFR06** | Hệ thống phải đảm bảo tính chính xác của tổng tiền hóa đơn. |
| **NFR07** | Hệ thống phải có khả năng sao lưu dữ liệu. |
| **NFR08** | Giao diện phải dễ sử dụng đối với Lễ tân và Nha sĩ. |

## 8. User Story

| ID | Role | User Story |
|---|---|---|
| **US01** | Bệnh nhân | Là Bệnh nhân, tôi muốn đặt lịch hẹn để có thể đăng ký thời gian khám phù hợp. |
| **US02** | Bệnh nhân | Là Bệnh nhân, tôi muốn hủy lịch hẹn để có thể thay đổi kế hoạch khám. |
| **US03** | Bệnh nhân | Là Bệnh nhân, tôi muốn xem lịch hẹn của mình để biết thời gian khám. |
| **US04** | Bệnh nhân | Là Bệnh nhân, tôi muốn xem hồ sơ khám của mình để biết lịch sử điều trị. |
| **US05** | Lễ tân | Là Lễ tân, tôi muốn đăng ký bệnh nhân để lưu thông tin bệnh nhân vào hệ thống. |
| **US06** | Lễ tân | Là Lễ tân, tôi muốn đặt lịch hẹn cho bệnh nhân để sắp xếp lịch khám không bị trùng. |
| **US07** | Lễ tân | Là Lễ tân, tôi muốn hủy lịch hẹn để cập nhật lịch làm việc chính xác. |
| **US08** | Lễ tân | Là Lễ tân, tôi muốn tạo hóa đơn để ghi nhận chi phí khám và điều trị. |
| **US09** | Lễ tân | Là Lễ tân, tôi muốn xác nhận thanh toán để cập nhật trạng thái hóa đơn. |
| **US10** | Nha sĩ | Là Nha sĩ, tôi muốn xem lịch làm việc để biết các bệnh nhân cần khám. |
| **US11** | Nha sĩ | Là Nha sĩ, tôi muốn ghi hồ sơ khám bệnh để lưu lại kết quả điều trị. |
| **US12** | Nha sĩ | Là Nha sĩ, tôi muốn xem hồ sơ bệnh nhân để biết lịch sử điều trị. |
| **US13** | Quản lý | Là Quản lý, tôi muốn quản lý dịch vụ và đơn giá để cập nhật danh mục nha khoa. |
| **US14** | Quản lý | Là Quản lý, tôi muốn xem báo cáo doanh thu để theo dõi tình hình hoạt động của phòng khám. |

# Phần II - Mô hình hóa quy trình

## 1. Activity Diagram – Đặt lịch hẹn

## 2. Activity Diagram – Khám bệnh và Thanh toán

## 3. Use Case Diagram

## 4. Đặc tả Use Case "Đặt lịch hẹn"

# 5. Đặc tả Use Case – Đặt lịch hẹn

| Thành phần | Nội dung |
|---|---|
| **Tên Use Case** | Đặt lịch hẹn |
| **Actor chính** | Bệnh nhân |
| **Actor phụ** | Lễ tân |
| **Mô tả** | Cho phép bệnh nhân đặt lịch khám với nha sĩ trong một ngày và khung giờ cụ thể. |
| **Tiền điều kiện** | Bệnh nhân đã có thông tin trong hệ thống; ngày hẹn hợp lệ. |
| **Hậu điều kiện** | Lịch hẹn được tạo và có trạng thái phù hợp. |

### Luồng chính

1. Bệnh nhân yêu cầu đặt lịch.
2. Hệ thống yêu cầu thông tin nha sĩ, ngày và khung giờ.
3. Bệnh nhân nhập thông tin.
4. Hệ thống kiểm tra ngày hẹn hợp lệ.
5. Hệ thống kiểm tra lịch của nha sĩ.
6. Hệ thống kiểm tra khung giờ có bị trùng hay không.
7. Nếu còn slot, hệ thống tạo Appointment.
8. Appointment có trạng thái `Chờ xác nhận`.
9. Hệ thống thông báo đặt lịch thành công.
10. Kết thúc Use Case.

### Luồng thay thế

**A1 – Khung giờ đã có lịch**

1. Hệ thống phát hiện slot không phù hợp.
2. Hệ thống thông báo khung giờ không còn phù hợp.
3. Hệ thống đề xuất khung giờ khác.
4. Bệnh nhân chọn lại hoặc kết thúc thao tác.

**A2 – Ngày hẹn không hợp lệ**

1. Hệ thống phát hiện ngày hẹn nhỏ hơn ngày hiện tại.
2. Hệ thống thông báo lỗi.
3. Bệnh nhân nhập lại ngày.

**A3 – Không thể đặt lịch**

1. Hệ thống không thể tạo lịch.
2. Hệ thống thông báo lỗi.
3. Use Case kết thúc.

### Hậu điều kiện

- Appointment được lưu trong hệ thống nếu đặt thành công.
- Appointment thuộc đúng một Patient.
- Appointment thuộc đúng một Dentist.
- Không tạo lịch bị trùng theo quy tắc nghiệp vụ.

# Phần III - Thiết kế cấu trúc tĩnh

# Phần IV - Mô hình hóa tương tác

## 1. Sequence Diagram - Đặt lịch hẹn

## 2. Sequence Diagram - Khám bệnh và Tạo hóa đơn

## 3. Sequence Diagram - Hủy lịch hẹn