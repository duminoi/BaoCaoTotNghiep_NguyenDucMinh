@startuml QuyTrinhDatHangVPP_Activity

start

:Truy cập bc.one-id.vn;

if (Đăng nhập thành công?) then (Có)
  :Chọn chương trình TPBANK MUA SẮM VPP;
  :Chọn sản phẩm;
  :Chọn chi nhánh;
else (Không)
  stop
endif

partition "Xử lý địa chỉ" {
  if (Đã có địa chỉ giao hàng?) then (Có)
    :Chỉnh sửa địa chỉ;
  else (Không)
    :Thêm mới địa chỉ;
  endif
}

:Vào giỏ hàng;

fork
  if (Ngày giao đúng điều kiện?) then (Có)
    :Xác nhận đặt hàng;
  else (Không)
    :Hệ thống tự chọn ngày;
  endif
fork again
  :Kiểm tra tồn kho;
end fork

if (Trạng thái đặt hàng?) then (Thành công)
  :Thông báo thành công;
else (Lỗi)
  :Thông báo lỗi;
  stop
endif

repeat
  :Tìm NCC phù hợp;
  repeat while (Đã gán NCC?) is (Không)
    ->Có;
  :NCC tiếp nhận đơn;
  :Đã đặt đơn;
  :Đang giao hàng;

  if (Giao hàng thành công?) then (Có)
    :Xác nhận tình trạng;
  else (Không)
    :Giao hàng thất bại;
    stop
  endif

  if (Kiểm tra đơn?) then (Đủ)
    :Xác nhận giao đủ;
  else (Lỗi)
    :Báo lỗi Thiếu/Thừa/Sai;
    :Xử lý bồi thường;
  endif
stop

@enduml