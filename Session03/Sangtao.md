Nhiệm vụ 1: Xác định Stakeholder trọng yếu
1. Xác định 3 nhóm Stakeholder

| Stakeholder | Vai trò trong tình huống | Quyền lực | Quan tâm | Ô Ma trận |
|---|---|---|---|---|
| **Bệnh nhân / Người nhà bệnh nhân** | Là người cần nhận thuốc cấp cứu và chịu ảnh hưởng trực tiếp nếu thuốc không được tiếp cận kịp thời. | Cao | Cao | **Quản lý chặt chẽ (Manage Closely)** |
| **Tài xế giao thuốc** | Trực tiếp có mặt tại địa chỉ bệnh nhân, thực hiện giao thuốc và xử lý bước liên lạc ban đầu. | Trung bình | Cao | **Giữ hài lòng (Keep Satisfied)** |
| **Điều phối viên RikkeiCare Emergency** | Theo dõi đơn hàng, nhận cảnh báo, quyết định chuyển cấp và hướng dẫn tài xế xử lý tình huống. | Cao | Cao | **Quản lý chặt chẽ (Manage Closely)** |

2. Lập luận lựa chọn
**Bệnh nhân / Người nhà bệnh nhân** được xếp vào ô **Quản lý chặt chẽ (Manage Closely)** vì có mức quan tâm và mức độ ảnh hưởng cao. Việc thuốc có được giao thành công hay không ảnh hưởng trực tiếp đến sức khỏe và tính mạng của bệnh nhân.
**Tài xế giao thuốc** được xếp vào ô **Giữ hài lòng (Keep Satisfied)** vì tài xế có mức quan tâm cao khi trực tiếp xử lý tình huống tại hiện trường. Tuy nhiên, tài xế không có quyền tự quyết định việc hủy đơn hoặc thay đổi phương án xử lý nên quyền lực được xếp ở mức trung bình.
**Điều phối viên RikkeiCare Emergency** được xếp vào ô **Quản lý chặt chẽ (Manage Closely)** vì có quyền theo dõi đơn hàng, tiếp nhận cảnh báo và quyết định phương án chuyển cấp. Đồng thời, điều phối viên phải đảm bảo ca cấp cứu được xử lý nhanh chóng và đúng quy trình.
Nhiệm vụ 2 - Tự thiết kế Cơ chế Ứng phó Unreachable Timeout Trap
1. Cơ chế chuyển cấp (Escalation Process) và Timeout

Khi tài xế xác nhận đã đến địa chỉ bệnh nhân nhưng không có người phản hồi, hệ thống sẽ bắt đầu **bộ đếm Timeout** và yêu cầu tài xế thực hiện các phương thức liên lạc như bấm chuông, gọi điện và liên hệ người nhận dự phòng nếu có. Khi Timeout kết thúc mà vẫn không có phản hồi, hệ thống tự động chuyển trạng thái đơn sang **“Không thể tiếp cận”** và gửi cảnh báo cho điều phối viên kèm vị trí hiện tại của tài xế. Điều phối viên kiểm tra thông tin người liên hệ dự phòng và hướng dẫn tài xế thực hiện phương án tiếp cận tiếp theo. Tài xế không được tự ý hủy đơn hoặc mang thuốc về khi chưa có quyết định xử lý từ điều phối viên.

2. Quy trình Escalation

| STT | Bước xử lý | Nội dung |
|---|---|---|
| **1** | **Xác nhận đến nơi** | Tài xế xác nhận đã đến đúng địa chỉ bệnh nhân và hệ thống bắt đầu tính thời gian Timeout. |
| **2** | **Thử liên lạc** | Tài xế bấm chuông, gọi điện và kiểm tra phương thức liên hệ dự phòng. |
| **3** | **Kích hoạt Timeout** | Nếu hết thời gian chờ nhưng không có phản hồi, hệ thống tự động chuyển đơn sang trạng thái **“Không thể tiếp cận”**. |
| **4** | **Chuyển cấp** | Hệ thống gửi cảnh báo cho điều phối viên cùng thông tin đơn hàng và vị trí tài xế. |
| **5** | **Xử lý tiếp theo** | Điều phối viên kiểm tra thông tin dự phòng và quyết định phương án xử lý tiếp theo. |

3. Nguyên tắc xử lý
**Không chờ vô thời hạn:** Hệ thống phải có Timeout rõ ràng khi tài xế đến địa chỉ nhưng không có phản hồi.
**Không tự ý hủy đơn:** Tài xế không được tự ý hủy hoặc mang thuốc về khi chưa có quyết định từ quy trình chuyển cấp.
**Tự động cảnh báo:** Khi Timeout kết thúc, hệ thống tự động gửi cảnh báo cho điều phối viên.
**Có phương án dự phòng:** Hệ thống sử dụng thông tin người liên hệ hoặc phương án bàn giao dự phòng đã được đăng ký trước.
**Chuyển quyền xử lý:** Sau Timeout, quyền quyết định được chuyển từ tài xế sang điều phối viên.
Nhiệm vụ 3 - Xác định Functional Requirement và Non-Functional Requirement
1. Functional Requirement (FR)

| STT | Yêu cầu | Loại yêu cầu |
|---|---|---|
| **1** | Khi tài xế xác nhận đã đến địa chỉ nhưng không có người phản hồi, hệ thống phải bắt đầu bộ đếm Timeout và tự động chuyển cấp khi Timeout kết thúc. | **Functional Requirement (FR)** |

FR-01 – Tự động chuyển cấp khi không thể liên lạc

Hệ thống phải tự động bắt đầu bộ đếm Timeout khi tài xế xác nhận đã đến địa chỉ bệnh nhân. Nếu hết thời gian Timeout mà người nhận vẫn không phản hồi, hệ thống phải chuyển trạng thái đơn sang **“Không thể tiếp cận”** và gửi cảnh báo cho điều phối viên kèm thông tin đơn hàng và vị trí của tài xế.

KPI đề xuất:

**100%** trường hợp tài xế xác nhận đã đến nơi phải được kích hoạt Timeout.
Hệ thống phải gửi cảnh báo cho điều phối viên trong vòng **≤ 5 giây** sau khi Timeout kết thúc.
2. Non-Functional Requirement (NFR)

| STT | Yêu cầu | Loại yêu cầu |
|---|---|---|
| **1** | Cơ chế Timeout và chuyển cấp phải hoạt động ổn định và không làm mất cảnh báo trong quá trình xử lý đơn cấp cứu. | **Non-Functional Requirement (NFR)** |

NFR-01 – Độ tin cậy vận hành

Hệ thống phải đảm bảo cơ chế Timeout và Escalation hoạt động ổn định trong quá trình xử lý đơn cấp cứu, hạn chế tối đa trường hợp mất sự kiện hoặc không gửi được cảnh báo chuyển cấp.

KPI/SLA đề xuất:

Tỷ lệ kích hoạt đúng Timeout và Escalation: **≥ 99,9%**.
Tỷ lệ mất sự kiện chuyển cấp: **≤ 0,1%**.
Thời gian gửi cảnh báo sau Timeout: **≤ 5 giây trong 99% trường hợp**.
3. Phân biệt FR và NFR

**Functional Requirement (FR)** mô tả **hệ thống phải làm gì**.

Ví dụ: Hệ thống phải bắt đầu Timeout, chuyển trạng thái đơn và gửi cảnh báo cho điều phối viên.

**Non-Functional Requirement (NFR)** mô tả **hệ thống phải hoạt động như thế nào**, ví dụ về độ tin cậy, hiệu năng, tốc độ và khả năng vận hành.

Nhiệm vụ 4 - Xây dựng User Story
1. Cấu trúc User Story

User Story được viết theo cấu trúc:

**Là một [Vai trò], Tôi muốn [Hành động], Để đạt được [Mục tiêu/Giá trị].**

Trong đó:

**Là một [Vai trò]**: Xác định người sử dụng chức năng.
**Tôi muốn [Hành động]**: Mô tả người dùng muốn hệ thống thực hiện điều gì.
**Để đạt được [Mục tiêu/Giá trị]**: Mô tả lợi ích mà người dùng nhận được.
2. User Story

| STT | Stakeholder | User Story |
|---|---|---|
| **1** | **Điều phối viên RikkeiCare Emergency** | **Là một Điều phối viên RikkeiCare Emergency, Tôi muốn nhận cảnh báo tự động khi tài xế không thể liên lạc với người nhận sau thời gian Timeout, Để nhanh chóng chuyển cấp và lựa chọn phương án xử lý tiếp theo nhằm đảm bảo bệnh nhân không bị bỏ lỡ thuốc cấp cứu.** |

3. Tại sao phần "Để [Mục tiêu/Giá trị]" là quan trọng?

Phần **“Để đạt được [Mục tiêu/Giá trị]”** giúp xác định **lý do và lợi ích thực tế** của chức năng đối với người dùng.

Trong bài toán RikkeiCare Emergency, mục tiêu không chỉ là gửi cảnh báo cho điều phối viên mà quan trọng hơn là giúp điều phối viên **nhanh chóng chuyển cấp và tiếp tục xử lý ca cấp cứu**, tránh để bệnh nhân không nhận được thuốc.

Phần **“Để đạt được [Mục tiêu/Giá trị]”** cũng giúp **Business Analyst, Developer và Tester** hiểu thống nhất mục tiêu của yêu cầu, từ đó xác định đúng phạm vi chức năng và xây dựng tiêu chí nghiệm thu phù hợp.