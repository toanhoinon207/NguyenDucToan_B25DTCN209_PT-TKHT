Phần 1 - Giải thích Vai trò UML & Lập Bảng định hướng Sơ đồ UML

1. Nêu 2 lý do tại sao sử dụng sơ đồ UML giúp Dev, BA và Tester không bị hiểu nhầm kịch bản hết hang
- UML mô tả luồng xử lý một cách trực quan
- UML tạo ra tài liệu chung giữa các bên:
+ BA dùng UML để mô tả nghiệp vụ. 
+ Dev dựa vào UML để lập trình. 
+ Tester dựa vào UML để xây dựng test case. 
+ Quản lý có thể nhìn vào UML để hiểu tổng quan hệ thống.

2. Lập Bảng định hướng danh mục sơ đồ UML cần vẽ
| Sơ đồ | Nhóm | Mục đích |
|---|---|---|
| **Use Case Diagram** | Behavioral | Xác định các Actor và các chức năng mà mỗi Actor sử dụng |
| **Activity Diagram** | Behavioral | Mô tả chi tiết luồng xử lý khi mua hàng, đặc biệt là trường hợp hết hàng và Timeout |
| **Class Diagram** | Structural | Mô tả các đối tượng/dữ liệu chính và quan hệ giữa chúng |

Phần 2 - Triển khai mã nguồn mô phỏng (Python)

def process_rikkeimart_order(item_status, customer_response):
    try:
        if item_status == "AVAILABLE":
            return "Sản phẩm còn hàng"
        if item_status == "OUT OF STOCK":
            print("Sản phẩm hết hàng")
            print("Tài xế đề xuất sản phẩm thay thế.")

            if customer_response == "YES":
                return "Khách đồng ý. Đổi sang sản phẩm thay thế"
            elif customer_response == "NO":
                return "Khách không đồng ý. Hủy sản phẩm"
            elif customer_response == "TIMEOUT":
                return "Timeout 3 phút. Tự động xử lý đơn an toàn."
            else:
                return "Phản hồi không hợp lệ."

        return "Trạng thái sản phẩm không hợp lệ."

    except Exception:
        return "Có lỗi xảy ra. Đơn hàng được xử lý an toàn."