# UX exercise — MoMo Moni AI

## Sản phẩm: MoMo Moni AI Assistant (phân loại chi tiêu tự động)

## 4 paths

### 1. AI đúng
- Khi xảy ra: giao dịch rõ ngữ cảnh, AI có độ tự tin cao.
- User thấy gì: giao dịch được gắn danh mục ngay, có icon nhóm chi tiêu, mục quan trọng được nổi bật.
- Hành vi AI: tự động phân loại và hiển thị tức thì, vẫn cho phép user chỉnh sửa nếu muốn.
- Nhận xét: flow nhanh, mượt, ít friction, tạo cảm giác tiện lợi.

### 2. AI không chắc
- Khi xảy ra: giao dịch mơ hồ, không đủ tín hiệu để phân loại chắc chắn.
- User thấy gì: hệ thống đưa gợi ý hoặc hỏi ngắn để user chọn danh mục.
- Hành vi AI: không tự quyết định khi confidence thấp, ưu tiên hỏi lại user.
- Vấn đề hiện tại: nếu không có bước xác nhận ngắn, user phải tự mò vào chỉnh sửa, dễ bỏ sót.
- Nguyên tắc UX: hỏi ngắn, đúng lúc, tránh làm phiền.

### 3. AI sai
- Khi xảy ra: AI gán nhầm danh mục, user phát hiện sau đó.
- User thấy gì: có điểm vào rõ để sửa danh mục; sau khi sửa, giao diện cập nhật ngay.
- Hành vi AI nên có: cho sửa thật nhanh, ghi nhận correction và áp dụng cho lần sau.
- Vấn đề hiện tại: chưa minh bạch AI có học từ chỉnh sửa hay không.
- Nhận xét: sai không phải tệ nhất, tệ nhất là sửa chậm và thiếu phản hồi.

### 4. User mất niềm tin
- Khi xảy ra: AI sai lặp lại hoặc kết quả vô lý.
- User thấy gì: tâm lý nghi ngờ, muốn thoát khỏi auto-flow.
- Hành vi AI nên có: cho chuyển sang manual mode, hiển thị dữ liệu gốc rõ ràng, không tiếp tục đoán bừa.
- Vấn đề hiện tại: thiếu lối thoát rõ ràng khi user không còn tin AI.
- Nhận xét: đây là critical path, nếu không có exit/fallback thì user rời bỏ tính năng.

## Path yếu nhất: Path 4 (kèm Path 3)

- Yếu nhất là giai đoạn sau khi AI sai nhiều lần.
- Recovery flow chưa đủ mạnh: thiếu manual-first mode, thiếu fallback rõ ràng.
- Feedback loop chưa minh bạch: user sửa nhưng không biết hệ thống có học hay không.
- Hệ quả: niềm tin giảm nhanh, user quay về thao tác thủ công hoàn toàn.

## Gap marketing vs thực tế

- Marketing hứa hẹn: quản lý chi tiêu thông minh, tự động, tiết kiệm công sức.
- Trải nghiệm thực tế: chạy tốt ở giao dịch quen thuộc, nhưng giao dịch mơ hồ vẫn cần can thiệp tay.
- Gap lớn nhất: marketing nhấn mạnh kết quả đúng, nhưng chưa nói rõ trải nghiệm khi AI không chắc hoặc AI sai.
- Tác động UX: user kỳ vọng gần như chính xác tuyệt đối, nên thất vọng mạnh khi gặp lỗi lặp lại và không thấy cơ chế phục hồi rõ ràng.

## Sketch

- As-is: giao dịch phát sinh -> AI auto-tag -> user xem kết quả -> nếu sai thì tự vào sửa.
- To-be: giao dịch phát sinh -> AI auto-tag.
- Nếu confidence thấp: hỏi ngắn để user chọn danh mục.
- Nếu user sửa: xác nhận đã ghi nhận correction và ưu tiên áp dụng cho lần sau.
- Nếu sai lặp lại: cho chuyển nhanh sang manual mode + hiển thị dữ liệu gốc + không ép AI đoán tiếp.
