# 04 — Reflection

**Học viên:** Chu Thị Ngọc Huyền — 2A202600015
**Nhóm:** Nhóm 4 — NestAI
**Ngày:** 12/05/2026

---

Sau Day 23, metric tôi sẽ sửa đầu tiên trong dashboard NestAI là **D14 menu compliance**. Ở v1, nhóm định nghĩa nó bằng **self-report duy nhất**: hỏi mẹ bầu "bạn đã ăn theo menu mấy ngày trong 2 tuần?". Sau red-team và sau khi nhìn lại case Morgan Stanley/Watson, tôi thấy đây gần như chắc chắn là **vanity metric**: mẹ bầu vừa được chẩn đoán GDM/IDA có động cơ trả lời "có" vì ngại với bác sĩ và với chính mình — đúng kiểu social desirability bias mà Watson đã trả giá khi tin vào "đã train trên N case" thay vì outcome thật.

Giả định tôi sẽ sửa là: "**self-report đủ để chứng minh compliance**". Sửa thành: compliance chỉ được tính khi có **ít nhất 1 signal khách quan** — photo log ≥ 3 ảnh/tuần, hoặc swap rate trong healthy band 1–3 món/menu, hoặc check-in giữa tuần với dietitian. Self-report đứng một mình bị bỏ.

Bài học sâu hơn: mỗi metric trong dashboard nên có cột "**proves / does not prove**" như Morgan Stanley làm với citation accuracy + 10–15h saved — không metric nào tự bảo vệ được kết luận, chỉ có **tổ hợp metric kèm signal khách quan** mới đứng vững trước CFO và Risk reviewer.

*(≈ 190 từ)*
