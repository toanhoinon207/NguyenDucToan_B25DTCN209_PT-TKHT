# Bước 1 – Soi lỗi thiết kế

- Thuộc tính bị trùng lặp
, hai lớp BacSi và YTa đều khai báo: `maNhanVien`, `hoTen`, `hoTen`, `soDienThoai`

--? Đây là các thuộc tính chung của nhân viên y tế.

Hậu quả

Khi cần sửa cấu trúc thuộc tính hoTen, phải sửa ở cả BacSi và YTa, làm tăng mã nguồn trùng lặp và khó bảo trì.

# Bước 2 – Tái cấu trúc bằng Inheritance

| **Lớp cha (Superclass)** | **Lớp con (Subclass)** | **Thuộc tính dùng chung** | **Thuộc tính riêng** |
|---|---|---|---|
| `NhanVienYTe` | `BacSi` | `maNhanVien`, `hoTen`, `soDienThoai` | `chuyenKhoa` |
| `NhanVienYTe` | `YTa` | `maNhanVien`, `hoTen`, `soDienThoai` | `khuVucTruc` |

# Bước 3 – Aggregation

**Multiplicity:** KhoaKham 1 ◇──────── 1..* NhanVienYTe

**Ý nghĩa:**

- Một KhoaKham có từ 1 đến nhiều NhanVienYTe.
- Nếu KhoaKham giải thể, NhanVienYTe vẫn tồn tại độc lập và có thể được chuyển sang khoa khác.

# Bước 4 – Sơ đồ Class Diagram