# Báo cáo cập nhật — Day 12 / G10 / Task 12 / Job 11

## E1 và kết quả kiểm tra

- Export CVAT mới ngày 23/11 được lưu trong gói là export_final_v2.zip. File nguồn là job_11_annotations_2026_11_23_02_19_03_cvat for images 1.1.zip.
- ZIP chỉ có annotations.xml, không kèm ảnh.
- Có đủ 22 ảnh và 22 tag frame_meta. Tổng 58 đối tượng: child_seat=8, face=10, face13=4, hand=11, infant_seat=10, object=4, person=10, phone=1.
- cabin_check.py check --expect 22 báo 0 lỗi, 0 cảnh báo.
- Kiểm tra hình học bổ sung trên export mới có 0 box suy biến hoặc vượt khung, 0 cặp box cùng class có IoU >= 0.70.
- So với export_final_v2.zip trước đó, thay đổi nhãn duy nhất là infant_seat.seat ở S07_ir đổi từ rear_left sang rear_right. Nhãn S07_rgb cũng là rear_right. Các khác biệt còn lại chỉ là thứ tự đối tượng và thời gian export.

## Giải thích face13 ở D01 và D03

- D01: Theo mô tả rà soát được cung cấp, mặt bị che khuất, không đủ căn cứ xác định chính xác các keypoint. Giữ box face và không tạo face13 bằng cách phỏng đoán.
- D03: Theo mô tả rà soát được cung cấp, mặt bị che khuất, không đủ căn cứ xác định vị trí các điểm đặc trưng. Không tạo skeleton chỉ để đủ 13 điểm.
- Căn cứ GUIDE §4.6: gắn cờ occluded khi vẫn xác định được vị trí điểm, outside khi không thể xác định điểm ở trong khung; không đặt điểm cho đủ số lượng.
- Đối chiếu XML của export xác nhận mỗi ảnh D01 và D03 có một box face và không có face13.
- Cần xác nhận trực tiếp tình trạng che khuất và khả năng nhìn điểm trên D01, D03 trong CVAT trước khi coi giải thích này là đã được rà soát trực quan. CVAT không mở được trong phiên cập nhật này, nên chưa xác nhận bằng mắt.

## Các chỉnh sửa và đối chiếu

- S02: đổi ghế trái ảnh sang infant_seat theo hình dáng nôi xách.
- S03_rgb và S03_ir: đổi túi thành object/bag; bỏ face và infant_seat ở vùng hình giống em bé theo quy tắc SVIRO.
- S04: bỏ child_seat gán nhầm, căn lại person và face.
- S07_ir: đổi infant_seat.seat sang rear_right, khớp với S07_rgb.
- S08_rgb: sửa infant_seat.seat từ driver sang rear_left.
- D02: bỏ face vẽ thừa.
- D04 và D06: bỏ face giả ở vùng tay, giữ nhãn hand tương ứng.
- export_final.zip vẫn là bản trước v2. Bản mới sau rà soát được lưu ở export_final_v2.zip.
- check_cpA.txt và check_cpB.txt là kiểm tra hồi cứu trên export mới cho S01-S02 và D01-D02, không phải log lịch sử tại checkpoint.
- check_final.txt giữ kết quả bản trước v2. check_final_v2.txt và check_final_v2.json được tạo lại từ export mới.
- Hồ sơ D01/D03 trong báo cáo dựa trên mô tả được cung cấp và kiểm tra cấu trúc XML. Việc xác nhận trực quan trong CVAT vẫn đang chờ.

## Hồ sơ E1–E5

| Tệp | Mã | Nội dung |
|---|---|---|
| export_final.zip, export_final_v2.zip | E1 | Hai export CVAT; chỉ chứa annotations.xml. |
| check_cpA.txt, check_cpB.txt, check_final.txt, check_final_v2.txt | E2 | Kiểm tra phạm vi checkpoint và kết quả cuối; provenance của log hồi cứu được ghi rõ. |
| disagreement_log.csv | E3 | 10 dòng có verdict, guideline_rule và action. |
| ir_log.csv | E4 | 4 quan sát, phân biệt real_IR và IR_sim. |
| class_list_v0.md | E5 | Có danh sách lớp DMS/OMS, mục đích sử dụng và 2 câu hỏi leo thang có ví dụ. |
| self_review.md, exit_ticket.md, TEAM.md, prompts.md | Bổ sung | Tự đánh giá, exit ticket, thông tin nhóm và khai báo sử dụng AI. |
| coach_escalations.md | Bổ sung | Ghi ca S03 cần hỏi coach; chưa gửi ghi chú cho coach. |

Gói hiện ở submission/K5-L2-DAY12-NguyenAnhTien-2A202603120-DMSOMS/. Các kiểm tra tự động xác nhận cấu trúc, thuộc tính theo schema và hình học cơ bản; chúng không thay thế việc rà từng nhãn bằng mắt trong CVAT.
