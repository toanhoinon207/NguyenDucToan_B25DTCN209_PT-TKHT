# Bước 1 — Phân loại 5 ghi chú thành yêu cầu chức năng/phi chức năng và xác định vị trí IEEE 830

| Ghi chú | Loại yêu cầu (Chức năng/Phi chức năng) | Vị trí IEEE 830 đề xuất |
|---|---|---|
| Ghi chú 1 | Chức năng (Functional) | 3.2 Functional Requirements |
| Ghi chú 2 | Phi chức năng (Non-functional) | 3.3 Non-Functional Requirements |
| Ghi chú 3 | Chức năng (Functional) | 3.2 Functional Requirements |
| Ghi chú 4 | Phi chức năng (Non-functional) | 3.3 Non-Functional Requirements |
| Ghi chú 5 | Phi chức năng (Non-functional) | 3.3 Non-Functional Requirements |

# Bước 2 — Xác định vị trí cho 2 sơ đồ đã có sẵn

| Sơ đồ | Vị trí IEEE 830 đề xuất | Lý do |
|---|---|---|
| Use Case Diagram tổng thể | 3.2 Functional Requirements | Mô tả Actor và các chức năng mà hệ thống cung cấp. |
| ERD Đơn hàng - Món ăn | 3.4 Database Requirements | Mô tả cấu trúc dữ liệu và quan hệ giữa các thực thể dữ liệu phục vụ hệ thống. |

# Bước 3 — Viết lại các ghi chú còn vi phạm đặc tính vàng

| Ghi chú | Đặc tính vàng bị vi phạm | Viết lại đạt chuẩn (có chỉ số/điều kiện cụ thể) |
|---|---|---|
| Ghi chú 2 | Verifiable | Sau khi khách hàng quét mã QR hợp lệ, hệ thống phải hiển thị thực đơn trong thời gian không quá 2 giây. |
| Ghi chú  | Unambiguous | Ứng dụng phải hỗ trợ 2 phiên bản mới nhất của Chrome, Safari và Edge trên thiết bị di động; các phiên bản cũ hơn không thuộc phạm vi hỗ trợ. |