# Tự đánh giá — Nguyen Anh Tien · G10

## 1. Tự rà soát 4 cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_rgb | Ghế bên trái ảnh | `wrong_class`, `seat_flip` | Mình đổi `child_seat` thành `infant_seat` và gọi seat theo chiều xe (`rear_right`). | Có |
| S03_ir | Túi và nôi | `wrong_class`, `extra` | Mình đổi box túi thành `object/bag`; bỏ `face` và `infant_seat` trên hình giống em bé theo quy tắc SVIRO. | Có |
| D02 | `person` | `box` | Mình mở lại ảnh, thấy box đủ ôm cơ thể nhìn thấy và giữ nguyên. | Có |
| D04 | `face` ở vùng tay | `wrong_class`, `missing` | Mình bỏ box face giả và gán `hand` cho bàn tay. | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Mình từng để thuộc tính seat mặc định `driver` trên ảnh SVIRO và đôi lúc gọi ghế theo phía ảnh.

Vì sao mình mắc: Mình chưa quy đổi vị trí từ góc camera sang chiều xe trước khi chọn seat.

Lần sau tránh bằng cách: Mình xác định ghế theo xe trước, sau đó kiểm tra lại từng `seat` bằng checker và đối chiếu guideline.

## 3. Ghi chú về disagreement_log

Reviewer đúng khi nhắc ghế bên trái ảnh S02 là `infant_seat` ở `rear_right`. Mình rút ra rằng trái/phải của ảnh không đồng nghĩa với trái/phải của xe; cần phân loại theo hình dáng ghế và quy ước hướng xe.
