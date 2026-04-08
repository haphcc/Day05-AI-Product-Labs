# Bài tập 1: tìm lỗi trong spec
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


---

## Phần 1 — Khám phá (15 phút)

**Trước khi dùng:** tìm hiểu sản phẩm marketing AI feature này thế nào — website, app store, bài PR. Sản phẩm hứa gì?

**Rồi dùng thử:** tải app / mở web, thử các tính năng AI. Quan sát kỹ: AI phản ứng thế nào? UI thay đổi gì? Có nút gì xuất hiện / biến mất?

1. Marketing
- Với mọi tiện ích tài chính trên Momo, nay bạn đã có thể quản lý tiền thảnh thơi hơn
- Đầu tư tiền đơn giản hơn
- Chi tiêu tiền thông minh hơn
- Tiếp cận tín dụng dễ dàng hơn
- Vận hành kinh doanh trơn chu hơn
- Duyệt khoản vay trong 1 phút
- An toàn bảo mật

## Test Case 1: Sai lệch thông tin (Hallucination Check)

Input:
“Viết lại nội dung marketing cho MoMo, nhấn mạnh việc duyệt khoản vay trong 1 phút và đầu tư dễ dàng”

Expected Output:
Có mention đúng:
“Duyệt khoản vay trong 1 phút”
“Đầu tư tiền đơn giản hơn”
Không tự thêm các thông tin không có trong spec (VD: lãi suất cụ thể, tên sản phẩm tài chính không tồn tại)
Không exaggerate kiểu: “duyệt ngay lập tức không cần điều kiện”

Fail nếu:
AI tự bịa thêm feature (ví dụ: “đầu tư crypto”, “lãi 15%/năm”)
Thay đổi meaning (ví dụ: từ “1 phút” → “ngay lập tức”)

*Test Case Success*

## Test Case 2: Quản lý tiền thực tế (Action-based Financial Assistance)

Input:
“Tôi có 10 triệu/tháng, chi tiêu trung bình 7 triệu. Hãy giúp tôi quản lý tiền sao cho vẫn tiết kiệm được và chi tiêu hợp lý hơn bằng MoMo”

Expected Output:
AI phải làm được 4 việc:

Phân tích tài chính cơ bản
Nhận ra: dư ~3 triệu/tháng
Xác định khả năng tiết kiệm
Đưa ra kế hoạch cụ thể (không chung chung)
Ví dụ:
2 triệu → tiết kiệm
1 triệu → quỹ dự phòng / chi tiêu linh hoạt
Gắn với value của MoMo (đúng spec)
Quản lý tiền thảnh thơi hơn (tracking chi tiêu)
Chi tiêu thông minh hơn
Không bịa thêm feature ngoài scope
Trình bày rõ ràng, dễ làm theo
Có thể dạng bullet / step
Không lý thuyết suông

Fail nếu:

Chỉ nói chung chung kiểu “hãy tiết kiệm nhiều hơn”
Không tính toán cụ thể từ input
Không đưa plan actionable
Hallucinate (VD: “MoMo tự đầu tư giúp bạn sinh lời”)
Không gắn với use case quản lý tiền

*Test Case Success*

Ok, dưới đây là **1 test case “hard mode”** cho tính năng **phân loại chi tiêu tự động** — loại này rất dễ làm AI fail trong production 👇

---

## Test Case 3 (Hard): Phân loại chi tiêu với dữ liệu nhiễu & mơ hồ

**Input:**
“Phân loại giúp tôi các giao dịch sau và cho biết tôi tiêu nhiều nhất vào đâu:

* 120k Highland ☕
* 2tr tiền nhà T3
* ck 500k cho Linh
* 89k Circle K
* 1.2m Shopee
* Grab 75k
* Apple.com/bill 49k
* 300k Winmart
* 200k ăn uống 🥲
* chuyển khoản 1tr”

---

**Expected Output:**

AI cần xử lý đúng **4 lớp khó**:

---

**1. Chuẩn hóa dữ liệu (Normalization)**

* 120k → 120,000
* 2tr → 2,000,000
* 1.2m → 1,200,000
* Hiểu emoji / viết tắt không ảnh hưởng logic

---

**2. Phân loại hợp lý (có xử lý ambiguity)**
Ví dụ:

* Ăn uống: Highland, ăn uống
* Sinh hoạt: tiền nhà
* Mua sắm: Shopee, Winmart, Circle K
* Di chuyển: Grab
* Khác / chưa rõ:

  * “ck 500k cho Linh” (có thể là chuyển tiền cá nhân)
  * “chuyển khoản 1tr” (thiếu context)
* Dịch vụ số:

  * Apple.com/bill (subscription / app)

👉 Quan trọng:
AI **không được đoán bừa**, phải có cách xử lý “unknown”

---

**3. Tổng hợp theo nhóm (có/không include ambiguous)**

* Phải rõ:

  * Tổng theo category
  * Có tách hoặc note phần “không xác định”

---

**4. Insight đúng & trung thực**

* Chi tiêu lớn nhất: nhiều khả năng là **tiền nhà** hoặc **mua sắm**
* Không được kết luận sai do bỏ qua ambiguity
* Có thể nói:

  > “Nếu tính cả các khoản chưa rõ, kết quả có thể thay đổi”

---

**Fail nếu:**

* ❌ Phân loại bừa:

  * “ck cho Linh” → ăn uống / mua sắm
* ❌ Không normalize số (2tr + 1.2m sai)
* ❌ Bỏ qua giao dịch mơ hồ
* ❌ Không cảnh báo ambiguity
* ❌ Insight sai vì cộng thiếu / sai
* ❌ Overconfident (kết luận chắc chắn khi data thiếu)

*Test Case Success*


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
