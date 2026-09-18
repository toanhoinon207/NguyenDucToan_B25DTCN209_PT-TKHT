| Tiêu chí | Tình huống A: `ChuyenXe` và `LoTrinh` | Tình huống B: `DonHang` và `CachThucThanhToan` |
|---|---|---|
| **Mô tả nghiệp vụ** | Một `ChuyenXe` có nhiều `LoTrinh`. Nếu Chuyến xe bị hủy, toàn bộ Lộ trình cũng bị hủy hoàn toàn theo, không tồn tại độc lập. | `DonHang` có phương thức `thanhToan()`, nhận đối tượng `CachThucThanhToan` chỉ để xử lý một lần, không lưu thành thuộc tính. |
| **Vòng đời dữ liệu** | Phụ thuộc hoàn toàn, "cùng sinh cùng tử" | **Tạm thời, không gắn vòng đời** |
| **Tên quan hệ** | **Composition** | **Dependency** |
| **Ký hiệu trên sơ đồ** | Hình thoi **đặc** đặt ở phía lớp **ChuyenXe** | Đường **nét đứt có mũi tên** trỏ từ **DonHang** sang **CachThucThanhToan** |

# Bước 1 – Kết luận phân biệt

- Composition là quan hệ gắn chặt về vòng đời: đối tượng thành phần không thể tồn tại độc lập khi đối tượng chứa bị hủy.
- Dependency chỉ thể hiện một lớp tạm thời sử dụng lớp khác để thực hiện một chức năng; hai đối tượng không phụ thuộc vào nhau về vòng đời.

# Bước 2 – Class Diagram