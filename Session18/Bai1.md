# Bước 1 — Xác định đúng vị trí IEEE 830 cho toàn bộ nội dung/sơ đồ

| Nội dung | Vị trí đề xuất | Đúng/Sai — vị trí đúng nếu sai |
|---|---|---|
| Mục A (định nghĩa "Giỏ hàng") | 3.2 Functional Requirements | Sai — đúng là 1.2 Definitions, Acronyms and Abbreviations |
| Mục B (3 yêu cầu chức năng) | 3.2 Functional Requirements | Đúng |
| Danh sách Actor/Use Case tổng thể | 3.2 Functional Requirements |  —  |
| Sơ đồ Sequence áp mã giảm giá (minh họa REQ-02) | 3.2 Functional Requirements |  —  |

# Bước 2 — Chuẩn hóa các yêu cầu chức năng theo đặc tính vàng

| Mã | Đặc tính vàng bị vi phạm | Viết lại đạt chuẩn |
|---|---|---|
| REQ-02 | Complete | Khi khách hàng nhập mã giảm giá, hệ thống phải kiểm tra mã còn hiệu lực và áp dụng đúng mức giảm đã được cấu hình. Nếu mã không hợp lệ hoặc hết hạn, hệ thống phải thông báo mã không thể áp dụng và không thay đổi tổng tiền đơn hàng. |
| REQ-03 | Verifiable | Hệ thống phải hoàn tất việc gửi yêu cầu thanh toán và hiển thị kết quả thanh toán trong tối đa 3 giây kể từ khi nhận được yêu cầu, trong điều kiện dịch vụ thanh toán hoạt động bình thường. |