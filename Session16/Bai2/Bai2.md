# Bước 1 - Xác định Entity, Attribute, Khóa chính

| Entity | Attribute cần lưu | Khóa chính (PK) đề xuất |
|---|---|---|
| HOC_VIEN | MaHV, HoTen, NgaySinh | MaHV |
| KHOA_HOC | MaKH, TenKH, SoTietHoc | MaKH |
| DANG_KY | MaHV, MaKH, DiemSo | MaHV, MaKH |

# Bước 2 - Vẽ quan hệ qua thực thể trung gian

# Bước 3 - Chuẩn hóa dữ liệu

- `TenKH` chỉ phụ thuộc vào `MaKH`, chỉ phụ thuộc vào một phần của khóa ghép (MaHV, MaKH) -> Vi phạm dạng chuẩn 2NF

**Cách tách bảng:**

**Bảng `KHOA_HOC`:**

| MaKH | TenKH | SoTietHoc |
|---|---|---|
| KH01 | Nhập môn Lập trình | - |
| KH02 | Thiết kế CSDL | - |

**Bảng `DANG_KY`:**

| MaHV | MaKH | DiemSo |
|---|---|---|
| HV01 | KH01 | 8.5 |
| HV02 | KH02 | 9.0 |
| HV02 | KH01 | 7.0 |