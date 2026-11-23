# Tình trạng hồ sơ Day 12 — G10

| Yêu cầu | Trạng thái | Ghi chú |
|---|---|---|
| E1 `export_final.zip` | Có | Snapshot trước v2, CVAT for images 1.1, chỉ có `annotations.xml`. |
| E1 `export_final_v2.zip` | Có | Bản sau review chéo, chỉ có `annotations.xml`. |
| E2 `check_final.txt` | Có | 0 lỗi; 3 cảnh báo trước v2 có giải thích riêng ở cuối file. |
| E2 `check_final_v2.txt` | Có | 0 lỗi, 0 cảnh báo; có QC hình học bổ sung. |
| E2 `check_cpA.txt`, `check_cpB.txt` | Có bản kiểm lại | Chạy hồi cứu trên v2 theo subset; không phải log checkpoint lịch sử vì mình không còn log gốc. |
| E3 `disagreement_log.csv` | Có | 10 dòng; `verdict`, `guideline_rule`, `action` đã điền. Mình xác nhận cốc S01 nhìn thấy rõ ở cả hai ảnh. |
| E4 `ir_log.csv` | Có | 4 quan sát; nguồn gồm `IR_sim` và `real_IR`. |
| E5 `class_list_v0.md` | Có | Có ít nhất 6 lớp DMS, 6 lớp OMS, mục đích sử dụng và 2 câu hỏi leo thang kèm khung ví dụ. |
| `self_review.md` | Có | Có 4 cảnh, lỗi lặp lại, nguyên nhân và cách tránh. |
| `exit_ticket.md` | Có | Có đầy đủ câu hỏi và câu trả lời theo mẫu. |
| `TEAM.md` | Có | G10, tên mình và reviewer Phan Hải Đăng. |
| `prompts.md` | Có | Khai báo không dùng model auto-label và ghi các lần dùng Codex/ChatGPT. |
| `coach_escalations.md` | Có | Ghi ca S03 để báo coach; mình chưa gửi ghi chú. |
| `export_extra.zip` | Không áp dụng | Mình không làm phần mở rộng S09–S10. |

## Ghi chú

- Log CP-A/CP-B là kiểm tra lại từ export cuối; không thay thế log lịch sử checkpoint.
- Mình đã khai báo trong `prompts.md` việc từng dùng ví dụ ảnh trong hội thoại AI. RULES §3 không cho đưa ảnh cabin cho AI; không có file ảnh nào trong thư mục nộp hay gói LMS.
- Mình đã xác nhận S01 cup ở cả hai ảnh và cập nhật `disagreement_log.csv`.
