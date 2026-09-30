# Bước 1 - Xác định Entity, Attribute, Khóa chính

| Entity | Attribute cần lưu | Khóa chính (PK) đề xuất |
|---|---|---|
| HOI_VIEN | MaHV, HoTen, SoDienThoai, NgayDangKy | MaHV |
| BUOI_TAP | MaBuoiTap, MaHV_FK, NgayTap, GioTap, TenHLV | MaBuoiTap |

# Bước 2 - Vẽ quan hệ bằng ký hiệu Chân quạ

# Bước 3 - Chuẩn hóa dữ liệu

- Cột `SoDienThoai` vi phạm dạng chuẩn 1NF vì 1 ô chứa nhiều số điện thoại: 0901111111, 0902222222 -> Không đảm bảo tính nguyên tử

**Cách tách bảng:** Tách số điện thoại là bảng riêng

**Bảng `HOI_VIEN`:**

| MaHV | HoTen | NgayDangKy |
|---|---|---|
| HV01 | Nguyễn Văn A | - |
| HV02 | Trần Thị B | - |

**Bảng `SDT_HOI_VIEN`:**

| MaHV (FK) | SoDienThoai |
|---|---|
| HV01 | 0901111111 |
| HV02 | 0902222222 |
| HV02 | 0903333333 |
