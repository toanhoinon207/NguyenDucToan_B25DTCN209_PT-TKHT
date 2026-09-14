# Phần 1 - Tóm tắt Nguyên nhân Thất bại
Hiệu năng: Hệ thống chưa tối ưu cơ chế xử lý và phân phối ảnh X-Quang/MRI dung lượng lớn, dẫn đến thời gian tải trung bình lên tới 48 giây.
Bảo mật: Dữ liệu hình ảnh bệnh án được truyền qua mạng mà không có cơ chế mã hóa, khiến thông tin y tế có nguy cơ bị đọc trộm khi bị bắt gói tin.
Khả dụng: Giao diện chưa được thiết kế phù hợp với người dùng cao tuổi, đặc biệt là cỡ chữ và kích thước nút "Hủy phiếu khám" quá nhỏ nên dễ thao tác nhầm.
# Phần 2 - Đề xuất Đa phương án Kỹ thuật & Trade-off
## 1. Đề xuất phương án kỹ thuật
### Phương án 1 - CDN + HTTPS/TLS + Image Optimization

Sử dụng CDN để phân phối hình ảnh gần người dùng, kết hợp nén/ tối ưu ảnh trước khi truyền và sử dụng HTTPS/TLS để mã hóa dữ liệu trong quá trình truyền tải.

### Phương án 2 - Object Storage + Signed URL + HTTPS/TLS

Lưu trữ ảnh xét nghiệm trên Object Storage, ứng dụng chỉ cấp Signed URL có thời hạn cho người dùng được phép truy cập và sử dụng HTTPS/TLS để bảo vệ dữ liệu khi truyền tải.

## 2. Bảng Trade-off

| Tiêu chí so sánh | Phương án 1: CDN + HTTPS/TLS + Image Optimization | Phương án 2: Object Storage + Signed URL + HTTPS/TLS | Lập luận đánh đổi |
|---|---|---|---|
| Thời gian phản hồi truy vấn | Nhanh nhờ CDN lưu bản sao gần người dùng và giảm kích thước ảnh khi truyền. | Nhanh, giảm tải cho Backend và có thể phân phối trực tiếp từ Object Storage. | Phương án 1 có lợi thế về tốc độ phân phối nhờ CDN, nhưng cần cơ chế đồng bộ và cache phù hợp. Phương án 2 giảm tải Backend tốt hơn nhưng phụ thuộc vào tốc độ Object Storage và việc tạo Signed URL. |
| Mức độ an toàn bảo vệ dữ liệu | Cao nhờ HTTPS/TLS mã hóa dữ liệu trên đường truyền, nhưng cần kiểm soát quyền truy cập CDN chặt chẽ. | Cao hơn nhờ Signed URL có thời hạn và giới hạn quyền truy cập từng tài nguyên, kết hợp HTTPS/TLS. | Phương án 2 bảo vệ quyền truy cập tài nguyên tốt hơn, nhưng việc quản lý token và thời hạn URL làm kiến trúc phức tạp hơn. |

## 3. Lựa chọn phương án tối ưu

Lựa chọn Phương án 2 - Object Storage + Signed URL + HTTPS/TLS vì vừa giảm tải cho Backend, hỗ trợ tải ảnh nhanh ở quy mô lớn, vừa kiểm soát quyền truy cập hình ảnh bệnh án bằng URL có thời hạn và đáp ứng yêu cầu bảo mật dữ liệu y tế.

# Phần 3 - Đặc tả Yêu cầu Phi chức năng (NFR)

| Nhóm NFR | Chỉ số định lượng mục tiêu | Tiêu chí nghiệm thu |
|---|---|---|
| Hiệu năng (Performance) | Thời gian tải ảnh xét nghiệm <= 1.5s | Thử nghiệm tải ảnh MRI 50MB hoàn thành trong 1.2s |
| Bảo mật (Security) | Mã hóa dữ liệu lưu trữ & truyền tải | Không thể giải mã gói tin khi bắt gói trung gian |
| Khả dụng (Usability) | Cỡ chữ >= 16pt, nút bấm >= 48px | 95% bệnh nhân > 60 tuổi thao tác thành công tự lực |
| Chịu tải (Scalability) | Hỗ trợ tối thiểu 3,000 người dùng đồng thời mà không bị sập | Kiểm thử tải với 3,000 người dùng đồng thời, hệ thống hoạt động ổn định và không xảy ra lỗi sập hệ thống |

# Phần 4 - Kết luận

Hệ thống cần ưu tiên tối ưu hiệu năng, bảo mật dữ liệu y tế và khả năng chịu tải, đồng thời cải thiện giao diện cho nhóm người dùng cao tuổi. Phương án Object Storage + Signed URL + HTTPS/TLS phù hợp hơn vì cân bằng được giữa tốc độ tải ảnh, khả năng mở rộng và mức độ bảo vệ dữ liệu.