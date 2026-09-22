# Phần 1 – Sắp xếp đúng thứ tự

| Thứ tự | Thông điệp | Loại |
|---|---|---|
| **1** | Khách hàng -> App Điều Phối: taoDonHang() | **Sync** |
| **2** | App Điều Phối -> Điện thoại Tài xế: Gửi yêu cầu nhận đơn | **Async** |
| **3** | Điện thoại Tài xế -> App Điều Phối: Phản hồi Đồng ý/Từ chối | **Message độc lập** |
| **4a** | **[Tài xế đồng ý]** App Điều Phối -> Trip: Khởi tạo bản ghi Chuyến Đi mới | **Create** |
| **4b** | **[Tài xế từ chối]** Không tạo Trip | — |
| **5** | App Điều Phối -> Khách hàng: Kết quả cuối cùng | **Return** |

