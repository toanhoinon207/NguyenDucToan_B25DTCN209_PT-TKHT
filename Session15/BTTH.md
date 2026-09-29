# Phần 1 - Xác định Entity/Attribute/Khóa chính

| Entity | Attribute cần lưu | Khóa chính (PK) |
|---|---|---|
| LOP_TAP | MaLop, TenLop, HocPhi | MaLop |
| HOI_VIEN | MaHoiVien, TenHoiVien, SoDienThoai | MaHoiVien |
| HUAN_LUYEN_VIEN | MaHLV, TenHLV | MaHLV |


# Phần 2 - Xác định quan hệ và Khóa ngoại

| Cặp Entity | Loại quan hệ | Khóa ngoại đặt ở Entity nào (nếu N-N thì nêu tên bảng trung gian) |
|---|:---:|---|
| HUAN_LUYEN_VIEN — LOP_TAP | 1 - N | FK MaHLV đặt trong LOP_TAP |
| HOI_VIEN — LOP_TAP | N - N | Tạo bảng DANG_KY_LOP, FK MaHoiVien, MaLop |

# Phần 3 - Xử lý 2 lỗi chuẩn hóa ở mục 4

| Lỗi ở mục 4 | Vi phạm dạng chuẩn nào | Tách thành bảng nào, gồm cột gì |
|---|:---:|---|
| TenLop, HocPhi chỉ phụ thuộc MaLop | 2NF | LOP_TAP(MaLop, TenLop, HocPhi) |
| SoDienThoai phụ thuộc TenHoiVien | 3NF | HOI_VIEN(MaHoiVien, TenHoiVien, SoDienThoai) |