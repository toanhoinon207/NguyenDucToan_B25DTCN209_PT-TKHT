# Phần 1 – Đề xuất 2 giải pháp

## Phương án 1: Kế thừa với Abstract Class `Payment`

**Tạo lớp cha:**

    Payment
    -------------------------
    paymentId: int
    amount: double
    paymentDate: Date
    -------------------------
    processPayment(): bool

**Các lớp con:**

    CreditCard
    -------------------------
    cardNumber: String
    cardHolder: String
    -------------------------
    processPayment(): bool

    EWallet
    -------------------------
    walletId: String
    provider: String
    -------------------------
    processPayment(): bool

    BankTransfer
    -------------------------
    bankAccount: String
    bankName: String
    -------------------------
    processPayment(): bool

**Quan hệ:** (CreditCard, EWallet, BankTransfer) `<<abstract>>` Payment

### Ưu điểm

- Thuộc tính chung chỉ khai báo **một lần** trong `Payment`.
- Các lớp con tái sử dụng được `paymentId`, `amount`, `paymentDate`.
- Mỗi lớp con tự viết `processPayment()` theo API riêng.
- Thêm `BankTransfer` mà không cần sửa code của `CreditCard` hoặc `EWallet`.
- Phù hợp với **DRY** và **Open/Closed Principle**.

### Nhược điểm

- Các phương thức thanh toán phải có quan hệ kế thừa với `Payment`.
- Nếu sau này một phương thức thanh toán có cấu trúc rất khác, mô hình kế thừa có thể trở nên kém linh hoạt.

## Phương án 2: Interface `IPayment`

Tạo Interface:

    <<interface>>
    IPayment
    -------------------------
    processPayment(): bool

Các lớp thanh toán thực hiện Interface:

    CreditCard ───────▷ IPayment

    EWallet ──────────▷ IPayment

    BankTransfer ─────▷ IPayment

Các thuộc tính chung được khai báo độc lập trong từng lớp:

    CreditCard
    -------------------------
    paymentId: int
    amount: double
    paymentDate: Date
    cardNumber: String
    -------------------------
    processPayment(): bool

    EWallet
    -------------------------
    paymentId: int
    amount: double
    paymentDate: Date
    walletId: String
    provider: String
    -------------------------
    processPayment(): bool

    BankTransfer
    -------------------------
    paymentId: int
    amount: double
    paymentDate: Date
    bankAccount: String
    bankName: String
    -------------------------
    processPayment(): bool

### Ưu điểm

- Rất linh hoạt.
- Mỗi phương thức thanh toán có thể triển khai `processPayment()` hoàn toàn khác nhau.
- Không bị giới hạn bởi quan hệ kế thừa.
- Dễ bổ sung phương thức thanh toán mới.

### Nhược điểm

- `paymentId`, `amount`, `paymentDate` phải khai báo lại ở nhiều lớp.
- Vi phạm phần nào nguyên tắc **DRY**.
- Khi thay đổi thuộc tính chung phải sửa nhiều Class.
- Mã nguồn có khả năng bị lặp.

---

# Phần 2 – Trade-off

| Tiêu chí | Phương án 1: Abstract Class | Phương án 2: Interface |
|---|---|---|
| Thuộc tính chung | **Tập trung ở Payment** | Phải khai báo ở từng Class |
| DRY | **Tốt** | Dễ bị lặp |
| processPayment() | Mỗi lớp con tự triển khai | Mỗi Class tự triển khai |
| Mở rộng | Dễ thêm phương thức mới | Dễ thêm phương thức mới |
| Bảo trì | **Dễ bảo trì thuộc tính chung** | Phải sửa nhiều Class nếu thuộc tính chung thay đổi |
| Tái sử dụng code | **Cao** | Thấp hơn |
| Tính linh hoạt | Thấp hơn Interface | **Cao** |
| Độ phức tạp | Đơn giản | Linh hoạt nhưng dễ lặp thuộc tính |
| Phù hợp bài toán | **Phù hợp** | Phù hợp nhưng có nhược điểm DRY |

# Phần 3 - Thiết kế