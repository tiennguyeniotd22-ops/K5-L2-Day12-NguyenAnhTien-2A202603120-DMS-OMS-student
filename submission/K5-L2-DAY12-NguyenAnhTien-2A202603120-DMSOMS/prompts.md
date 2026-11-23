# Khai báo dùng AI — Nguyen Anh Tien

Mình **không dùng model auto-label**. Trong quá trình làm bài, mình có dùng Codex/ChatGPT để hỗ trợ theo các mục dưới đây.

| # | Công cụ | Mình hỏi gì (tóm tắt) | Mình dùng kết quả thế nào | Mình kiểm lại bằng gì? |
|---|---|---|---|---|
| 1 | Codex/ChatGPT | Mình hỏi cách hiểu guideline về class, thuộc tính, hướng mắt, seat và cách đọc kết quả checker. | Mình dùng phần giải thích để tự sửa nhãn trên CVAT; không dùng AI để sinh nhãn tự động. | Mình đối chiếu với Guideline Cabin v1.0 và chạy `cabin_check.py --expect 22`. |
| 2 | Codex/ChatGPT | Mình hỏi class/thuộc tính cho các ví dụ ảnh do mình gửi trong hội thoại. | Mình dùng câu trả lời để hiểu quy tắc và tự quyết định nhãn. Việc gửi ảnh cabin cho AI không phù hợp RULES §3; mình ghi nhận rõ và không đưa ảnh vào repo/GitHub. | Mình đối chiếu lại với guideline; checker chỉ xác nhận schema, không dùng làm bằng chứng thị giác. |
| 3 | Codex/ChatGPT | Mình nhờ rà format ZIP, tổng hợp kết quả tự kiểm và chỉnh câu chữ hồ sơ. | Mình dùng kết quả để hoàn thiện báo cáo, log và gói nộp. | Mình kiểm tra ZIP chỉ chứa `annotations.xml`, rà file trong thư mục nộp và xem output checker. |
