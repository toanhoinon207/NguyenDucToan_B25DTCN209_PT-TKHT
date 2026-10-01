# Bước 1 — Xác định đúng vị trí IEEE 830

| Nội dung | Vị trí đề xuất | Đúng/Sai — vị trí đúng nếu sai |
|---|---|---|
| Mục A (định nghĩa SKU) | 2.4 Constraints | Sai — đúng là 1.2 Definitions, Acronyms and Abbreviations |
| Mục B (3 yêu cầu chức năng) | 3.2 Functional Requirements | Đúng |
| Danh sách Actor/Use Case tổng thể | 3.1 External Interfaces | Sai — đúng là 3.2 Functional Requirements |
| Sơ đồ Sequence quét mã vạch (minh họa REQ-02) | 3.2 Functional Requirements | Sai — đúng là 3.2 Functional Requirements |

# Bước 2 — Viết lại REQ-02 và REQ-03 đạt chuẩn Verifiable

| Mã | Từ ngữ cảm tính | Viết lại (có chỉ số đo lường cụ thể) |
|---|---|---|
| REQ-02 | "cực nhanh" | Khi quét mã vạch sản phẩm, hệ thống phải hiển thị kết quả xử lý trong không quá 2 giây kể từ thời điểm nhận được mã vạch hợp lệ. |
| REQ-03 | "nếu thấy cần thiết" | Hệ thống phải cho phép người dùng có quyền Quản lý kho thực hiện xuất báo cáo tồn kho theo yêu cầu. |
