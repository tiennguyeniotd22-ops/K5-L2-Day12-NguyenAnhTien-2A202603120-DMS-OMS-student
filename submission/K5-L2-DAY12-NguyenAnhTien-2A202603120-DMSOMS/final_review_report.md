# Báo cáo hoàn tất — Day 12 / G10 / Task 12 / Job 11

## Kết quả cuối cùng

- **File nộp:** `export_final_v2.zip`, export từ CVAT ngày 23/11. ZIP hợp lệ, chỉ chứa `annotations.xml`, không kèm ảnh.
- **Số lượng nhãn:** đủ 22/22 ảnh và 22 tag `frame_meta`. Tổng cộng 58 đối tượng: `child_seat=8`, `face=10`, `face13=4`, `hand=11`, `infant_seat=10`, `object=4`, `person=10`, `phone=1`.
- **Tự kiểm:** `cabin_check.py check --expect 22` báo **0 lỗi, 0 cảnh báo**.
- **Hình học:** không có box suy biến hoặc vượt khung ảnh; không có cặp box cùng class có IoU >= 0.70. Mình đã tự rà box `person` D01–D06, thấy độ ôm sát ổn và giữ nguyên.

## Các điểm mình đã sửa sau review chéo

- **S02:** Mình đổi ghế bên trái sang `infant_seat` theo hình dáng nôi xách.
- **S03 (`S03_rgb`, `S03_ir`):** Mình đổi túi thành `object/bag`; xóa box `face` và `infant_seat` ở vị trí hình giống em bé theo quy tắc SVIRO. Mình không đổi hình đó thành `person`.
- **S04:** Mình xóa box `child_seat` gán nhầm, bổ sung và căn lại box `person` và `face`.
- **S08_rgb:** Mình sửa `infant_seat.seat` từ `driver` sang `rear_left`.
- **D02:** Mình xóa box `face` bị vẽ thừa và giữ box `person` đã tự rà lại.
- **D04, D06:** Mình xóa các box `face` gán nhầm vào vùng tay và tách nhãn thành `hand`.

## Đối chiếu giữa bản đầu và bản v2

- `export_final.zip` trước khi sửa có 0 lỗi và 3 cảnh báo `infant_seat seat=driver` tại S03_ir, S03_rgb và S08_rgb.
- Trong `export_final_v2.zip`, mình bỏ hai box ở S03 theo quy tắc SVIRO và sửa `seat` ở S08_rgb thành `rear_left`; checker báo 0 lỗi, 0 cảnh báo.
- Mình không còn log lịch sử Checkpoint A/B. `check_cpA.txt` và `check_cpB.txt` trong gói là kết quả chạy lại trên export cuối, lọc theo S01–S02 và D01–D02. Mình đã ghi rõ đây là log chạy lại, không phải log lịch sử.
- Mình không dùng model auto-label. Mình gán nhãn bằng tay và có dùng Codex/ChatGPT để tra guideline, giải thích thuộc tính và kiểm tra export; mình khai báo việc này trong `prompts.md`.

## Ghi chú các ca đặc biệt

- **S03_ir / S03_rgb:** Mình đã ghi ca có hình giống trẻ em vào `coach_escalations.md` để báo coach theo guideline. Mình chưa gửi ghi chú cho coach.
- **S01_ir / S01_rgb:** Mình đã kiểm tra lại phần nghi vấn ở lượt review trước. Mình xác nhận chiếc cốc nhìn thấy rõ trên cả ảnh RGB và IR, nên giữ `object` với `type=cup` ở cả hai ảnh.

## Hồ sơ theo `SUBMISSION.md`

| Tên file | Mã | Nội dung |
|---|---|---|
| `export_final.zip` | E1 | Bản trước v2, CVAT for images 1.1, không kèm ảnh. |
| `export_final_v2.zip` | E1 | Bản sau review chéo, không kèm ảnh. |
| `check_cpA.txt` | E2 | Check lại subset S01–S02 trên export cuối; không phải log lịch sử CP-A. |
| `check_cpB.txt` | E2 | Check lại subset D01–D02 trên export cuối; không phải log lịch sử CP-B. |
| `check_final.txt` | E2 | 0 lỗi; 3 cảnh báo của bản trước v2 có giải thích riêng ở cuối file. |
| `check_final_v2.txt` | E2 | 0 lỗi, 0 cảnh báo; có QC hình học bổ sung. |
| `disagreement_log.csv` | E3 | 10 dòng có `verdict`, `guideline_rule` và `action`, lưu CSV UTF-8. |
| `ir_log.csv` | E4 | 4 quan sát, phân biệt nguồn `real_IR` và `IR_sim`. |
| `class_list_v0.md` | E5 | Có lớp DMS/OMS, mục đích sử dụng và 2 câu hỏi leo thang kèm khung ví dụ. |
| `self_review.md` | — | Mình nêu lỗi lặp lại, nguyên nhân và cách tránh theo mẫu. |
| `exit_ticket.md` | — | Mình đã điền đáp án trên mẫu đầy đủ. |
| `TEAM.md` | — | Mình ghi mã G10 và bạn review chéo Phan Hải Đăng. |
| `prompts.md` | — | Mình khai báo các lần dùng Codex/ChatGPT và xác nhận không dùng model auto-label. |
| `coach_escalations.md` | — | Mình ghi ca S03 để hỏi coach; chưa gửi ghi chú. |
| `export_extra.zip` | Tùy chọn | Mình không làm phần mở rộng S09–S10. |

Mình lưu hồ sơ trong `submission/K5-L2-DAY12-NguyenAnhTien-2A202603120-DMSOMS/`. ZIP để nộp LMS nằm cùng cấp với thư mục này. Các kiểm tra tự động xác nhận format và hình học cơ bản; chúng không thay thế đánh giá nội dung từng nhãn bằng mắt.
