# Phần 1 – Bảng so sánh ưu/nhược điểm

| **Tiêu chí** | **Giải pháp 1 – Virtual Queue** | **Giải pháp 2 – Rate Limiting** |
|---|---|---|
| **Cách hoạt động** | Đưa khách hàng vào phòng chờ ảo, cứ mỗi 10 giây cho tối đa 500 khách vào thanh toán. | Nếu lượng request vượt 5.000 requests/giây thì hệ thống từ chối request mới. |
| **Mức độ giảm tải Server** | **Rất tốt**. Request được phân phối theo từng đợt 500 người, giúp kiểm soát lượng request đến hệ thống thanh toán. | **Tốt**. Chặn request vượt ngưỡng giúp bảo vệ server nhưng lượng request bị từ chối có thể tăng đột biến. |
| **Trải nghiệm khách hàng (UX)** | **Tốt hơn**. Khách hàng biết mình đang ở trong hàng đợi và có thể chờ đến lượt. | **Thấp hơn**. Khách hàng có thể nhận thông báo "Hệ thống bận, thử lại sau" và phải tự thao tác lại. |
| **Khả năng xử lý Flash Sale** | **Tốt**. Phù hợp với trường hợp có hàng trăm nghìn khách truy cập cùng lúc. | **Khá**. Có thể bảo vệ hệ thống nhưng không điều phối được lượng khách vào thanh toán theo từng đợt. |
| **Chi phí triển khai** | **Cao hơn** do cần xây dựng hệ thống hàng đợi, quản lý vị trí và trạng thái khách hàng. | **Thấp hơn** vì chủ yếu cần cơ chế giới hạn request. |
| **Độ phức tạp** | **Cao**. Phải quản lý hàng đợi, thời gian chờ, trạng thái và trường hợp hết hàng. | **Thấp hơn**. Logic chính là kiểm tra số lượng request và từ chối khi vượt ngưỡng. |
| **Xử lý khi hết hàng** | Có thể chủ động thông báo cho toàn bộ khách đang chờ và giải tán phòng chờ. | Khách hàng đã bị từ chối request không có trạng thái chờ để hệ thống quản lý. |
| **Nhược điểm chính** | Khách hàng phải chờ và hệ thống phải xử lý thêm logic hàng đợi. | Dễ gây cảm giác hệ thống bị lỗi vì khách nhận thông báo bận và phải thử lại. |

---

# Phần 2 – Chốt giải pháp

## Lựa chọn: Virtual Queue – Hàng đợi ảo

RikkeiShop nên lựa chọn **Giải pháp 1 – Virtual Queue** vì giải pháp này phù hợp hơn với đặc điểm của chương trình Flash Sale có hơn 100.000 khách hàng truy cập cùng lúc. Thay vì cho toàn bộ khách hàng gửi request thanh toán đồng thời, hệ thống đưa khách vào phòng chờ và chỉ cho tối đa **500 khách hàng mỗi 10 giây** thực hiện thanh toán, từ đó kiểm soát tải và hạn chế tình trạng cổng thanh toán bị Crash.

Mặc dù chi phí và độ phức tạp triển khai cao hơn Rate Limiting, Virtual Queue mang lại trải nghiệm tốt hơn vì khách hàng biết mình đang được xếp hàng thay vì liên tục nhận lỗi "Hệ thống bận, thử lại sau". Ngoài ra, giải pháp còn có thể chủ động xử lý trường hợp sản phẩm hết hàng bằng cách thông báo và giải tán phòng chờ.

# Phần 3 – Activity Diagram

## Edge Case – Hết hàng khi đang chờ

Trong thời gian khách hàng đang ở phòng chờ:

- Kiểm tra tồn kho → **Hết hàng** → Hệ thống thông báo **"Hết hàng"** → Giải tán phòng chờ ảo → Kết thúc.

https://drive.google.com/file/d/13_Va6OsOHgbOaCu6vavMwFQ2qLzFxgL2/view?usp=drive_link