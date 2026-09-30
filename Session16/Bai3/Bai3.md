# Bước 1 - Xác định Entity, Attribute, Khóa chính

| Entity | Attribute cần lưu | Khóa chính (PK) đề xuất |
|---|---|---|
| CAN_HO | MaCH, DienTich, SoTang, MaKhuVuc_FK | MaCH |
| HOP_DONG_THUE | MaHD, NgayBatDau, NgayKetThuc, MaCH_FK | MaHD |
| KHU_VUC | MaKhuVuc, TenKhuVuc | MaKhuVuc |

# Bước 2 - Vẽ 2 loại quan hệ

# Bước 3 - Chuẩn hóa dữ liệu

- `TenKhuVuc` phụ thuộc bắc cầu vào `MaCH` thông qua `MaKhuVuc`. -> Vi phạm dạng chuẩn NF

**Cách tách bảng:**

**Bảng `CAN_HO`:**

| MaCH | DienTich | MaKhuVuc |
|---|---|---|
| CH01 | 45 | KV01 |
| CH02 | 60 | KV01 |
| CH03 | 50 | KV02 |

**Bảng `KHU_VUC`:**

| MaKhuVuc | TenKhuVuc |
|---|---|
| KV01 | Quận 1 |
| KV02 | Quận 7 |