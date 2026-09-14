# Nhiệm vụ 1: Phân tích Môi trường Hệ thống và Xác định Stakeholders

## 1. Môi trường hoạt động của hệ thống

| Nhóm môi trường | Mô tả |
|---|---|
| **1. Môi trường kinh doanh tại nhà hàng** | QuickBite được triển khai tại chuỗi nhà hàng Cơm Tấm Sài Gòn gồm **15 chi nhánh tại TP.HCM**. Hệ thống hỗ trợ tiếp nhận đơn hàng, quản lý món ăn, xử lý đơn tại nhà bếp, giao hàng và xem báo cáo doanh thu. |
| **2. Môi trường kỹ thuật hạ tầng/di động** | Hệ thống gồm **ứng dụng di động cho khách hàng**, **ứng dụng di động cho tài xế** và **hệ thống POS cho nhà hàng**. Hệ thống cần Internet, máy chủ, cơ sở dữ liệu, thanh toán trực tuyến và bản đồ định vị. |
| **3. Môi trường con người** | Hệ thống có nhiều nhóm người sử dụng như **khách hàng, chủ nhà hàng, nhân viên bếp, tài xế và quản trị viên**. Mỗi nhóm có nhu cầu, nhiệm vụ và quyền sử dụng hệ thống khác nhau. |

## 2. Xác định Stakeholder

| Stakeholder | Nguồn yêu cầu phù hợp | Nhu cầu cốt lõi |
|---|---|---|
| **Khách hàng** | Nguồn con người, nguồn thị trường/đối thủ | Tìm món ăn, đặt món, thanh toán online, theo dõi đơn hàng và nhận hàng thuận tiện. |
| **Chủ nhà hàng** | Nguồn con người, nguồn tài liệu, nguồn hệ thống hiện tại | Tiếp nhận đơn hàng, quản lý menu, xem báo cáo doanh thu và giảm sai sót trong quá trình xử lý đơn. |
| **Tài xế** | Nguồn con người, nguồn hệ thống hiện tại | Nhận đơn giao hàng, xem thông tin đơn, xem bản đồ chỉ đường và quản lý thu nhập. |
| **Quản trị viên** | Nguồn con người, nguồn tài liệu, nguồn hệ thống hiện tại | Quản lý tài khoản, phân quyền, giám sát hệ thống và đảm bảo hệ thống hoạt động ổn định, an toàn. |

# Nhiệm vụ 2 - Lựa chọn kỹ thuật thu thập yêu cầu

| STT | Tình huống | Kỹ thuật phù hợp | Lý do |
|---|---|---|---|
| **1** | Tìm hiểu cấu trúc nhóm món ăn và giá từ các hóa đơn giấy cũ. | **Phân tích tài liệu (Document Analysis)** | Hóa đơn giấy cũ là tài liệu thực tế, có thể cung cấp thông tin về tên món, nhóm món và giá bán. |
| **2** | Tìm hiểu quy trình phối hợp thực tế giữa đầu bếp và nhân viên chuẩn bị món trong bếp. | **Quan sát (Observation)** | Quan sát trực tiếp giúp biết được quy trình thực tế, các bước xử lý và những thao tác có thể không được ghi trong tài liệu. |
| **3** | Tìm hiểu những vấn đề về quản lý doanh thu và mong muốn của chủ nhà hàng. | **Phỏng vấn chuyên sâu (In-depth Interview)** | Phỏng vấn chuyên sâu cho phép đặt câu hỏi, hỏi thêm và làm rõ các vấn đề về quản lý doanh thu cũng như nhu cầu của chủ nhà hàng. |
| **4** | Thu thập ý kiến về phí giao hàng từ 1.000 tài xế trên toàn thành phố. | **Khảo sát diện rộng (Broad Survey)** | Có thể thu thập ý kiến của số lượng lớn tài xế trong thời gian ngắn và dễ dàng tổng hợp, thống kê kết quả. |

## Tại sao không sử dụng phỏng vấn chuyên sâu cho 1.000 tài xế?

Không nên sử dụng **phỏng vấn chuyên sâu** vì phải dành rất nhiều thời gian và chi phí để phỏng vấn từng tài xế. Ngoài ra, việc sắp xếp lịch phỏng vấn với 1.000 người cũng khó khăn và kết quả khó tổng hợp.

Trong trường hợp này, **khảo sát diện rộng** phù hợp hơn vì có thể thu thập ý kiến của nhiều tài xế trong thời gian ngắn và dễ dàng thống kê kết quả.

# Nhiệm vụ 3 - Phân loại Functional Requirement và Non-Functional Requirement

## 1. Phân loại yêu cầu

| STT | Yêu cầu | Loại yêu cầu |
|---|---|---|
| **1** | Khách hàng có thể gõ từ khóa để tìm kiếm món ăn trên ứng dụng. | **Functional Requirement (FR)** |
| **2** | Thời gian hiển thị kết quả tìm kiếm phải dưới 1.5 giây. | **Non-Functional Requirement (NFR)** |
| **3** | Chủ nhà hàng có thể bấm xác nhận tiếp nhận đơn hàng trên màn hình POS. | **Functional Requirement (FR)** |
| **4** | Ứng dụng phải chịu tải 10.000 người dùng truy cập cùng lúc. | **Non-Functional Requirement (NFR)** |
| **5** | Giao dịch thanh toán thẻ phải được mã hóa truyền tải an toàn. | **Non-Functional Requirement (NFR)** |
| **6** | Tài xế có thể bật/tắt chế độ sẵn sàng nhận đơn hàng mới. | **Functional Requirement (FR)** |

**Functional Requirement (FR)** mô tả **hệ thống phải làm gì**.

**Non-Functional Requirement (NFR)** mô tả **hệ thống phải hoạt động như thế nào**, ví dụ về tốc độ, hiệu năng và bảo mật.

## 2. Bổ sung KPI/SLA cho các NFR

| STT | Non-Functional Requirement | KPI/SLA |
|---|---|---|
| **1** | Thời gian hiển thị kết quả tìm kiếm phải dưới 1.5 giây. | Ít nhất **95% yêu cầu tìm kiếm** phải trả về kết quả trong thời gian **dưới 1.5 giây**. |
| **2** | Ứng dụng phải chịu tải 10.000 người dùng truy cập cùng lúc. | Hệ thống phải hỗ trợ tối thiểu **10.000 người dùng đồng thời**, với ít nhất **95% yêu cầu được xử lý thành công**. |
| **3** | Giao dịch thanh toán thẻ phải được mã hóa truyền tải an toàn. | **100% dữ liệu giao dịch thanh toán thẻ** phải được truyền qua kết nối bảo mật **TLS 1.2 trở lên**. |

# Nhiệm vụ 4 - Xây dựng User Story

## 1. Cấu trúc User Story

User Story được viết theo cấu trúc:

**Là một [Vai trò], Tôi muốn [Hành động], Để [Mục tiêu/Giá trị].**

Trong đó:

- **Là một [Vai trò]**: Xác định người sử dụng chức năng.
- **Tôi muốn [Hành động]**: Mô tả người dùng muốn hệ thống thực hiện điều gì.
- **Để [Mục tiêu/Giá trị]**: Mô tả lợi ích mà người dùng nhận được.

## 2. Danh sách User Story

| STT | Stakeholder | User Story |
|---|---|---|
| **1** | **Khách hàng** | **Là một Khách hàng, Tôi muốn tìm kiếm món ăn theo từ khóa, Để nhanh chóng tìm được món ăn mình muốn đặt.** |
| **2** | **Khách hàng** | **Là một Khách hàng, Tôi muốn theo dõi trạng thái đơn hàng, Để biết đơn hàng của mình đang được xử lý và giao đến đâu.** |
| **3** | **Chủ nhà hàng** | **Là một Chủ nhà hàng, Tôi muốn xác nhận tiếp nhận đơn hàng trên màn hình POS, Để nhà bếp có thể bắt đầu chuẩn bị món cho khách hàng.** |
| **4** | **Chủ nhà hàng** | **Là một Chủ nhà hàng, Tôi muốn xem báo cáo doanh thu, Để theo dõi tình hình kinh doanh của nhà hàng.** |
| **5** | **Tài xế** | **Là một Tài xế, Tôi muốn bật hoặc tắt chế độ sẵn sàng nhận đơn hàng mới, Để chủ động quyết định thời điểm mình có thể nhận đơn giao hàng.** |
| **6** | **Tài xế** | **Là một Tài xế, Tôi muốn xem bản đồ chỉ đường đến địa điểm giao hàng, Để giao đơn hàng đến khách hàng nhanh chóng và chính xác.** |

## 3. Tại sao phần "Để [Giá trị]" là quan trọng nhất?

Phần **"Để [Giá trị]"** giúp xác định **lý do và lợi ích thực tế** của chức năng đối với người dùng.

Nó giúp nhóm phát triển hiểu được tại sao chức năng đó cần được xây dựng, từ đó tránh việc tạo ra những chức năng không mang lại giá trị thực tế.

Ngoài ra, phần **"Để [Giá trị]"** còn giúp **Business Analyst, Developer và Tester** hiểu thống nhất mục tiêu của yêu cầu, hỗ trợ việc ưu tiên chức năng và xây dựng tiêu chí nghiệm thu phù hợp.