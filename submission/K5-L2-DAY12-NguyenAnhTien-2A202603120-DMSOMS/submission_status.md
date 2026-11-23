# Tình trạng hồ sơ Day 12 — G10

| Yêu cầu | Trạng thái | Ghi chú |
|---|---|---|
| E1 export_final.zip | Có | Snapshot trước v2, CVAT for images 1.1, chỉ chứa annotations.xml. |
| E1 export_final_v2.zip | Đã cập nhật | Dùng export mới ngày 23/11. Đủ 22 ảnh, 22 frame_meta, 0 lỗi và 0 cảnh báo. |
| E2 check_final.txt | Có | Kết quả bản trước v2, có giải thích 3 cảnh báo. |
| E2 check_final_v2.txt | Đã chạy lại | Checker trên export mới, có bổ sung kiểm tra hình học và đối chiếu XML D01/D03. |
| E2 check_cpA.txt, check_cpB.txt | Đã chạy lại | Kiểm tra hồi cứu trên export mới; không phải log lịch sử checkpoint. |
| E3 disagreement_log.csv | Có | 10 dòng đã điền verdict, guideline_rule và action. |
| E4 ir_log.csv | Có | 4 quan sát, có real_IR và IR_sim. |
| E5 class_list_v0.md | Có | Có ít nhất 6 lớp DMS, 6 lớp OMS, chức năng và 2 câu hỏi leo thang có ví dụ. |
| self_review.md, exit_ticket.md, TEAM.md, prompts.md | Có | Các hồ sơ bổ sung đã được điền. |
| coach_escalations.md | Có | Ca S03 đã ghi; chưa gửi ghi chú cho coach. |
| D01/D03 face13 | Chờ xác nhận trực quan | XML có box face và không có face13 ở cả hai ảnh; cần xác nhận lý do che khuất trực tiếp trong CVAT. |

## Ghi chú

- Export mới chỉ chứa annotations.xml, không có ảnh.
- So với export v2 cũ, nhãn thay đổi là S07_ir infant_seat.seat sang rear_right, khớp với S07_rgb.
- Việc không gán face13 D01/D03 dựa trên mô tả rà soát đã cung cấp. Phiên cập nhật này chưa xác nhận trực quan trong CVAT.
- Gói ZIP nộp LMS được làm mới cùng với các báo cáo để phản ánh export mới.
