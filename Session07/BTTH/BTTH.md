# Nhiệm vụ 1: Nhận diện Lớp và Khai báo Cấu trúc 3 ngăn

## 1. Xác định 4 Lớp

- Customer – Khách hàng
- Order – Đơn hàng
- MenuItem – Món ăn
- Employee – Nhân viên

## 2. Khai báo cấu trúc 3 ngăn

### Class Customer

| Customer |
|---|
| - customerId: int |
| - name: String |
| - email: String |
| - phone: String |
|---|
| + getName(): String |
| + getEmail(): String |
| + createOrder(): Order |

### Class Order

| **Order** |
|---|
| - orderId: int |
| - orderDate: Date |
| - status: String |
| - totalAmount: double |
|---|
| + addItem(): void |
| + calculateTotal(): double |
| + applyVoucher(): void |

### Class MenuItem

| **MenuItem** |
|---|
| - itemId: int |
| - name: String |
| - price: double |
| - stock: int |
|---|
| + updatePrice(): void |
| + updateStock(): void |

### Class Employee

| **Employee** |
|---|
| - employeeId: int |
| - name: String |
| - email: String |
| - phone: String |
|---|
| + getName(): String |
| + getEmail(): String |

# Nhiệm vụ 2: Thiết lập Bổ từ truy cập và Bảo vệ Dữ liệu

| **Ký hiệu** | **Visibility** | **Ý nghĩa** |
|---|---|---|
| `+` | Public | Có thể truy cập từ bên ngoài |
| `-` | Private | Chỉ được truy cập bên trong lớp |
| `#` | Protected | Lớp hiện tại và lớp kế thừa có thể truy cập |
| `~` | Package | Truy cập trong cùng package |

# Nhiệm vụ 3: Phân tích và Lựa chọn Mối quan hệ giữa các Lớp