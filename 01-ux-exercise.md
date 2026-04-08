Đề tài 2: AI tóm tắt meeting
-- Lỗi AI có thể mắc phải khi tóm tắt meeting
1. Gán sai người chịu trách nhiệm (Wrong Accountability Assignment)
2. Tóm tắt sai ý chính (Missing or Distorted Key Points)
3. Nhầm lẫn giữa hành động và thảo luận (Action Misclassification)
4. Tự suy diễn thông tin không tồn tại (Hallucinated Tasks / Owners)

-- Các User Path đang thiếu trong spec
1. Không có bước kiểm tra trước khi gửi kết quả
Quy trình hiện tại thiếu bước để người dùng xem lại và chỉnh sửa nội dung trước khi chia sẻ. Điều này khiến mọi sai sót từ AI có thể bị lan truyền ngay lập tức đến các bên liên quan.
2. Thiếu cơ chế xác nhận khi AI không chắc chắn
Khi gặp thông tin mơ hồ, hệ thống không có cách để hỏi lại người dùng mà vẫn đưa ra kết luận. Việc không xử lý các trường hợp “không chắc” khiến AI dễ đưa ra dự đoán sai thay vì giữ trạng thái trung lập.
3. Không có hệ thống nhận diện và liên kết người tham gia
Spec chưa đề cập cách liên kết giữa tên trong cuộc họp và thông tin thực tế như email hoặc vai trò. Điều này khiến AI khó hiểu được ai đang nói và vai trò của họ trong ngữ cảnh công việc.

# Bài tập UX: phân tích sản phẩm AI thật

**Thời gian:** 40 phút | **Cá nhân** | **Output:** sketch giấy, nộp cuối bài

---

## Chọn 1 sản phẩm

| Sản phẩm | AI feature | Truy cập |
|----------|-----------|---------|
| MoMo — Trợ thủ AI Moni | Phân loại chi tiêu, chatbot tài chính | App MoMo |
| Vietnam Airlines — Chatbot NEO | Chatbot hỗ trợ khách hàng, tra cứu chuyến bay | vietnamairlines.com hoặc Zalo VNA |
| V-App — Trợ lý ảo V-AI | Trợ lý voice/text, gợi ý theo context | App V-App |

---

## Phần 1 — Khám phá (15 phút)

**Trước khi dùng:** tìm hiểu sản phẩm marketing AI feature này thế nào — website, app store, bài PR. Sản phẩm hứa gì?

**Rồi dùng thử:** tải app / mở web, thử các tính năng AI. Quan sát kỹ: AI phản ứng thế nào? UI thay đổi gì? Có nút gì xuất hiện / biến mất?

## Phần 2 — Phân tích 4 paths (10 phút)

Dùng framework 4 paths để mổ xẻ sản phẩm:

| Path | Câu hỏi |
|------|---------|
| 1. Khi AI **đúng** | User thấy gì? Hệ thống confirm thế nào? |
| 2. Khi AI **không chắc** | Hệ thống xử lý thế nào? Im lặng? Hỏi lại? Show alternatives? |
| 3. Khi AI **sai** | User biết bằng cách nào? Sửa bằng cách nào? Bao nhiêu bước? |
| 4. Khi user **mất tin** | Có exit không? Có fallback (con người, manual)? Dễ tìm không? |

**Tự phân tích:**
- Path nào sản phẩm xử lý tốt nhất? Tại sao?
- Path nào yếu nhất hoặc không tồn tại?
- Kỳ vọng từ marketing khớp thực tế không? Gap ở đâu?

## Phần 3 — Sketch "làm tốt hơn" (10 phút)

Chọn **1 path yếu nhất** mà mình tìm được. Sketch trên giấy:

- **As-is** (bên trái): user journey hiện tại → đánh dấu chỗ gãy
- **To-be** (bên phải): user journey đề xuất → vẽ kế bên
- Ghi rõ: thêm gì? Bớt gì? Đổi gì?

Không cần đẹp. Cần rõ.

## Phần 4 — Share + vote (5 phút)

Chia sẻ sketch với nhóm. Mỗi người trình bày ngắn (30 giây). Nhóm vote sketch hay nhất → **bonus điểm**.

---

## Nộp bài

Mỗi người nộp sketch giấy + ghi chú phân tích 4 paths. Đây là **điểm cá nhân**.

**Nice to have:** screenshot màn hình app + annotate (khoanh, ghi chú) chỗ hay / chỗ gãy. Nộp kèm sketch.

---

## Tiêu chí chấm (10 điểm + bonus)

| Tiêu chí | Điểm |
|----------|------|
| Phân tích 4 paths đủ + nhận xét path yếu nhất | 4 |
| Sketch as-is + to-be rõ ràng | 4 |
| Nhận xét gap marketing vs thực tế | 2 |
| **Bonus:** nhóm vote sketch hay nhất | +bonus |

---

*Bài tập UX — Ngày 5 — VinUni A20 — AI Thực Chiến · 2026*
