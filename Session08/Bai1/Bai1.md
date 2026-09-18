# Bước 1 – Trích xuất Lớp, Thuộc tính và Phương thức

| Thành phần | Lớp Customer | Lớp Order |
|---|---|---|
| **Thuộc tính** | `customerId`, `fullName`, `phone` | `orderId`, `createdDate` |
| **Phương thức** | `placeOrder()` | `calculateTotal()` |

# Bước 2 – Access Modifier và Multiplicity

- **Thuộc tính:** private --> ký hiệu -
- **Phương thức:** public --> ký hiệu +
- **Quan hệ:** Association

**Multiplicity:**

`Customer` 1 ───────── 0..* `Order`

**Nghĩa là:**  Một Customer có thể có 0 hoặc nhiều Order, và mỗi Order chỉ thuộc về 1 Customer.