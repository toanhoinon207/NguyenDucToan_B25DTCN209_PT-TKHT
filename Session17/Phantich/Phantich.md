# Phần 1

## Giải pháp 1 — Sync API

RikkeiLogistics gọi trực tiếp API của Cổng thanh toán để tạo/kiểm tra giao dịch và chờ kết quả trả về ngay trong cùng request.

Khách hàng -> RikkeiLogistics App -> Payment API -> Cổng thanh toán -> Kết quả thanh toán -> RikkeiLogistics

**Ưu điểm:** kiến trúc đơn giản, dễ triển khai và dễ theo dõi trạng thái giao dịch.

**Nhược điểm:** khi mạng hoặc Cổng thanh toán chậm, request có thể timeout; phải xử lý trường hợp khách đã bị trừ tiền nhưng RikkeiLogistics chưa nhận được kết quả.

## Giải pháp 2 — Async Webhook/Queue

RikkeiLogistics tạo giao dịch, sau khi thanh toán thành công Cổng thanh toán gửi Webhook. Webhook được đưa vào Message Queue, sau đó Worker xử lý bất đồng bộ.

Khách hàng -> RikkeiLogistics App -> Cổng thanh toán -> Message Queue -> Consumer Worker -> Billing Service -> Cập nhật đơn hàng

**Ưu điểm:** không phụ thuộc vào việc kết nối trực tiếp phải duy trì lâu; Queue giúp hấp thụ lượng lớn Webhook và cho phép retry khi xử lý lỗi.

**Nhược điểm:** phức tạp hơn, phải xử lý HMAC, Idempotency, retry, duplicate Webhook và trạng thái giao dịch.

## Bảng Trade-off

| Tiêu chí | Giải pháp 1 — Sync API | Giải pháp 2 — Async Webhook/Queue |
|---|---|---|
| **Độ tin cậy khi nghẽn mạng** | Thấp hơn: request có thể timeout dù giao dịch đã thành công | Cao hơn: Webhook được đưa vào Queue và có thể retry xử lý |
| **Độ phức tạp triển khai** | Thấp: luồng xử lý trực tiếp | Cao: cần Queue, Consumer, retry, idempotency |
| **Rủi ro sai lệch dữ liệu tài chính** | Có rủi ro nếu timeout sau khi khách bị trừ tiền | Có thể kiểm soát bằng HMAC + Idempotency Key + ACID + Audit Log |
| **Phù hợp tải lớn** | Khó mở rộng khi số request đồng thời tăng cao | Phù hợp hơn vì Queue có thể hấp thụ lượng Webhook lớn |

## Giải pháp được chọn

**Giải pháp 2 — Async Webhook/Queue**

**Lý do:** bài toán có trên 200.000 giao dịch/ngày, đồng thời phải xử lý timeout và Webhook gửi trùng. Queue cho phép tách việc nhận sự kiện thanh toán khỏi việc xử lý nghiệp vụ, còn HMAC + Idempotency Key + ACID + Audit Trail giúp kiểm soát tính toàn vẹn của giao dịch tài chính.

# Phần 2

# Phần 3

## 4 bảng dữ liệu

| Bảng | Mục đích |
|---|---|
| **Shipment** | Lưu thông tin vận đơn và trạng thái đơn hàng, trong đó có trạng thái `PAID`. |
| **PaymentTransaction** | Lưu giao dịch thanh toán, mã giao dịch, số tiền, trạng thái và Idempotency Key. |
| **CODSettlement** | Lưu thông tin đối soát COD và trạng thái chuyển tiền cho người gửi. |
| **AuditLog** | Lưu lịch sử các thao tác và sự kiện tài chính để truy vết. |

## Cơ chế bảo mật

**API Key:** dùng để xác thực ứng dụng RikkeiLogistics khi gọi API của Cổng thanh toán. API Key phải được bảo mật và không đưa trực tiếp vào mã nguồn công khai.

**HMAC-SHA256:** Cổng thanh toán tạo chữ ký từ dữ liệu giao dịch và secret key. RikkeiLogistics dùng secret key tương ứng để kiểm tra chữ ký trước khi xử lý giao dịch. Chỉ khi HMAC hợp lệ mới được phép gạch nợ và chuyển trạng thái PAID.