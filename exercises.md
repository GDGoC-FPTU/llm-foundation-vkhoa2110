# Ngày 1 - Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) -> Bài tập mở rộng (30 phút)

---

## Phần 1 - Lập Trình Cốt Lõi (0:00-1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 - Bài Tập Mở Rộng (1:00-1:30)

### Bài tập 2.1 - Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2-3 câu)
> Ở temperature thấp như 0.0, phản hồi thường ổn định, trực tiếp và ít biến thể hơn. Khi tăng lên 0.5, 1.0 và 1.5, câu trả lời có xu hướng sáng tạo hơn, cách diễn đạt đa dạng hơn, nhưng cũng dễ lan man hoặc đưa chi tiết kém chắc chắn hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2-0.3 cho chatbot hỗ trợ khách hàng, vì nhóm tác vụ này cần câu trả lời nhất quán, đúng chính sách và ít rủi ro bịa thông tin hơn là cần sáng tạo.

---

### Bài tập 2.2 - Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload có 10.000 x 3 = 30.000 lượt gọi/ngày, tương đương khoảng 10,5 triệu token/ngày. Theo bảng giá trong `template.py`, GPT-4o đắt hơn GPT-4o-mini khoảng 33,3 lần cho cả input và output, nên tỷ lệ chi phí của workload này cũng xấp xỉ 33,3 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng hơn khi bài toán cần chất lượng suy luận cao, xử lý yêu cầu phức tạp hoặc phản hồi có ảnh hưởng lớn đến người dùng/doanh nghiệp, ví dụ phân tích tài liệu quan trọng hoặc trợ lý chuyên môn. GPT-4o-mini phù hợp hơn cho tác vụ khối lượng lớn, rủi ro thấp và cần tối ưu chi phí như FAQ, phân loại intent, tóm tắt ngắn hoặc chatbot tuyến đầu.

---

### Bài tập 2.3 - Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang tương tác trực tiếp, vì họ thấy nội dung xuất hiện ngay và cảm giác chờ đợi giảm rõ rệt, ví dụ chatbot, trợ lý viết code hoặc câu trả lời phân tích nhiều bước. Non-streaming phù hợp hơn với phản hồi ngắn, xử lý batch, API backend cần nhận đủ kết quả để validate/parse JSON, hoặc các tác vụ không cần hiển thị tức thời.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
