# Phần 1 

## 1. COMBO

| Attribute | Data  | Key |
|---|:---:|:---:|
| ComboID | INT | PK |
| ComboName | VARCHAR(100) | |
| Price | DECIMAL(10, 2) | |

## 2. BRANCH 

| Attribute | Data  | Key |
|---|:---:|:---:|
| BranchID | INT | PK |
| BranchName | VARCHAR(100) | |

## 3. BOOKING_COMBO

| Attribute | Data  | Key |
|---|:---:|:---:|
| BookingComboID | INT | PK |
| BookingID | INT | FK -> BOOKING |
| ComboID | INT | FK -> COMBO |
| BranchID | INT | FK -> BRANCH |
| Quantity | INT | |
| UnitPrice | DECIMAL(10, 2) | |

# Phần 2

# Phần 3

COMBO không lưu tồn kho trực tiếp; BranchID được lưu cùng thông tin mua Combo để phân biệt Combo được bán tại từng cơ sở, tránh dùng chung một số lượng tồn kho cho toàn chuỗi.

BOOKING_COMBO lưu UnitPrice tại thời điểm mua, nên khi giá Combo thay đổi thì các Booking cũ vẫn giữ nguyên giá đã mua.