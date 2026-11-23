# Danh sách lớp v0 — Nguyen Anh Tien · G10

Mình lập danh sách này theo Guideline Cabin v1.0; mỗi dòng nêu mục đích sử dụng và khả năng quan sát trên IR.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` / `seat`, `seatbelt` | driver; worn_correct, worn_incorrect, not_worn, unknown | Xác định tài xế và tình trạng dây an toàn để hỗ trợ cảnh báo an toàn | Thấy dáng người; dây có thể chìm trong bóng tối nên dùng unknown khi không rõ |
| 2 | `face` | box mặt; eye_left/right, glasses, gaze_zone | Định vị mặt để theo dõi trạng thái mắt và hướng nhìn | Thường thấy vùng mặt; kính/phản xạ/tay che có thể làm mất chi tiết |
| 3 | `eye_left`, `eye_right` | open, closed, unknown | Nhận biết mắt nhắm/mở để phát hiện dấu hiệu buồn ngủ | Có thể thấy trên NIR; phản xạ/kính tối khiến trạng thái unknown |
| 4 | `gaze_zone` | road, mirror_l/r/c, cluster, center, lap, other | Nhận biết tài xế nhìn đường hay nhìn khỏi vùng đường | Hướng đầu/mắt thường thấy; vùng chính xác có thể không rõ |
| 5 | `face13` | 13 điểm; occluded/outside | Định vị điểm mặt phục vụ phân tích tư thế và trạng thái mắt | Thấy nếu mặt đủ lớn và không bị che; không đoán điểm |
| 6 | `hand` | whose, side, on_wheel | Nhận biết tay tài xế/hành khách và tay có chạm vô lăng không | Thường thấy hình dạng tay; trái/phải tính theo người |
| 7 | `phone` | held, mounted, lap | Phát hiện hành vi dùng điện thoại khi lái xe | Chỉ gán khi thấy hình dạng điện thoại; không dựa riêng vào màu tối |
| 8 | `seatbelt` | worn_correct, worn_incorrect, not_worn, unknown | Phân loại cách đeo dây an toàn | Dải dây có thể thấy trong IR nhưng tương phản thấp; không rõ thì unknown |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` / `seat` | driver, front_passenger, rear_left, rear_middle, rear_right | Xác định người và vị trí ngồi để kiểm tra phân bố người trong cabin | Thường thấy dáng người; seat gọi theo xe |
| 2 | `face` | box mặt người lớn | Xác nhận vùng mặt của người trong cabin cùng box person | Thấy nếu mặt không bị che và đủ sáng |
| 3 | `child_seat` | seat; occupied=no/unknown | Xác định ghế trẻ em và tình trạng lòng ghế | Hình ghế thường thấy; lòng ghế bị tối/che thì occupied=unknown |
| 4 | `infant_seat` | seat; facing=front/rear | Phân biệt nôi xách với ghế trẻ em theo hình dạng và hướng | Quai/khung ghế có thể thấy; không dùng màu IR để đoán |
| 5 | `object` | seat; type=bag/box/cup/other | Xác định đồ vật để quên trong cabin | Hình dạng/vị trí có thể thấy; loại vật chỉ gán khi đủ căn cứ |
| 6 | `seat` | driver/front_passenger/rear_left/rear_middle/rear_right | Gắn đúng vật/người với vị trí ghế trên xe | Vị trí ảnh quan sát được; cần quy đổi góc camera sang chiều xe |
| 7 | `occupied`, `facing` | no/unknown; front/rear | Mô tả lòng ghế trẻ em trống hay không rõ và hướng nôi | Dựa vào hình lòng ghế/quai; không suy từ ảnh cặp nếu không thấy |
| 8 | `frame_meta` | modality, light, camera_blocked | Lưu ngữ cảnh ảnh để diễn giải dữ liệu nhất quán | modality theo tên file; light/blocked chỉ chọn khi có căn cứ |

## Câu hỏi leo thang

1. Câu hỏi: Ở S03_ir/S03_rgb, nôi có hình giống em bé nhưng guideline nói SVIRO không gán trẻ em và infant_seat chỉ cho nôi trống. Có cần gửi coach duyệt ca này sau khi bỏ box `face` và `infant_seat` không?
   Khung ví dụ: `S03_ir` và `S03_rgb`.
   Mình tạm xử lý: không gán hình giống em bé, bỏ các box liên quan, không đổi thành `person`, và ghi ca để báo coach.
2. Câu hỏi: Vật tại rear_middle của S01 có thể nhận dạng là cốc trong cả IR-sim và RGB hay chỉ nên gán ở ảnh nào nhìn rõ?
   Khung ví dụ: `S01_ir` / `S01_rgb`.
   Mình tạm gán `object/type=cup` riêng trên ảnh mà hình dạng đủ nhận biết; không sao chép nhãn nếu vật không thấy rõ.
