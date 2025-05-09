@startuml
actor "Người dùng" as User
actor "Nhà cung cấp" as Vendor
actor "Hệ thống" as System

User --> (Đăng nhập)
User --> (Chọn chương trình)
User --> (Chọn sản phẩm)
User --> (Chọn chi nhánh)
User --> (Quản lý địa chỉ giao hàng)
User --> (Vào giỏ hàng)
User --> (Chọn ngày giao hàng)
User --> (Xác nhận đặt hàng)
User --> (Xác nhận giao đủ)
User --> (Báo lỗi sản phẩm)
User --> (Gửi báo cáo lỗi)

(System) --> (Tự động chọn ngày giao nếu sai điều kiện)
(System) --> (Thông báo kết quả đặt hàng)
(System) --> (Kiểm tra NCC sản phẩm & địa chỉ)
(System) --> (Chuyển đơn hàng đến NCC)

(Vendor) --> (Tiếp nhận đơn hàng)
(Vendor) --> (Cập nhật trạng thái đơn hàng)
Vendor --> (Xác nhận giao hàng thành công/thất bại)

(System) --> (Xác nhận bồi thường)
(System) --> (Chờ xử lý tiếp nếu không bồi thường)

(Báo lỗi sản phẩm) --> (Chọn lỗi)
(Chọn lỗi) --> (Nhập chi tiết lỗi)
(Nhập chi tiết lỗi) --> (Gửi báo cáo lỗi)
@enduml
