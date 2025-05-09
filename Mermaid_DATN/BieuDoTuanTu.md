@startuml
|Người dùng|
start
:Truy cập bc.one-id.vn;
:Đăng nhập;
:Chọn chương trình TPBANK MUA SẮM VPP;
:Chọn sản phẩm;
:Chọn chi nhánh;

:Kiểm tra địa chỉ giao hàng;
if (Đã có địa chỉ?) then (Có)
  :Chỉnh sửa địa chỉ;
else (Không)
  :Thêm mới địa chỉ;
endif

:Vào giỏ hàng;
:Chọn ngày giao hàng;
if (Ngày giao hàng đúng điều kiện?) then (Đúng)
  :Xác nhận đặt hàng;
else (Sai)
  |Hệ thống|
  :Hệ thống tự chọn ngày;
endif

|Hệ thống|
if (Đặt hàng thành công?) then (Có)
  :Thông báo thành công;
else (Không)
  :Thông báo lỗi;
  stop
endif

|Hệ thống|
:Kiểm tra NCC cho sản phẩm;
if (Có NCC?) then (Có)
  :Kiểm tra NCC cho địa chỉ;
else (Chưa có)
  :Gán NCC cho sản phẩm;
endif

if (Có NCC địa chỉ?) then (Có)
  :Chuyển giao đơn cho NCC;
else (Chưa có)
  :Gán NCC cho địa chỉ;
endif

:NCC tiếp nhận đơn;
:NCC chuyển trạng thái đơn;
:Đơn hàng đang giao;

|Người dùng|
if (Giao hàng thành công?) then (Đã giao)
  :Xác nhận tình trạng giao hàng;
else (Giao thất bại)
  stop
endif

:Kiểm tra đơn hàng;
if (Đủ?) then (Đủ)
  :Xác nhận giao đủ;
else (Thiếu/Thừa/Sai sản phẩm/Sai địa chỉ)
  :Báo lỗi sản phẩm;
  :Chọn loại lỗi;
  :Nhập chi tiết số lượng/mô tả lỗi;
  :Gửi báo cáo lỗi;
endif

|Hệ thống|
if (Cần bồi thường?) then (Có)
  :Xác nhận bồi thường;
else (Không)
  :Chờ xử lý tiếp;
endif
stop
@enduml
