# 01 — Case Evidence Matrix

**Học viên:** Chu Thị Ngọc Huyền — 2A202600015
**Nhóm:** Nhóm 4 — NestAI
**Case được phân tích:** **Morgan Stanley AI Assistant** (GPT-4 cho ~16.000 financial advisors)
**Ngày:** 11/05/2026

---

## 1. Tóm tắt case

Morgan Stanley hợp tác với OpenAI để xây **AI @ Morgan Stanley Assistant** dựa trên GPT-4 cho hơn 16.000 financial advisors (FA). Hệ thống truy cập hơn 100.000 tài liệu nội bộ (research, compliance, product). Tính năng **AI @ Morgan Stanley Debrief** sinh meeting notes, action items và draft email; advisor là người chỉnh sửa và gửi với sự đồng ý của khách. CEO Ted Pick (Reuters, 2024) phát biểu AI có thể giúp advisor tiết kiệm **10–15 giờ/tuần**. CDO Magazine ghi **98%** advisors WM dùng AI chatbot.

---

## 2. Evidence matrix — đọc metric từ case

| Câu hỏi | Trả lời | Nguồn |
|---|---|---|
| AI được dùng trong workflow nào? | (1) FA hỏi nghiệp vụ → AI trích dẫn tài liệu nội bộ. (2) Soạn nháp tóm tắt client meeting. (3) Tạo action items và draft email sau meeting. (4) FA review/chỉnh sửa trước khi gửi khách hoặc lưu vào Salesforce. | [Forbes / Davenport 2023](https://www.forbes.com/sites/tomdavenport/2023/03/20/how-morgan-stanley-is-training-gpt-to-help-financial-advisors/); [Morgan Stanley Debrief launch](https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch) |
| Họ công bố / được ghi nhận metric gì? | • Quy mô triển khai: >16.000 FA, >100.000 docs. • Adoption: 98% WM advisors dùng AI chatbot (CDO Magazine, phỏng vấn Atul Dalmia). • Productivity proxy: 10–15 giờ tiết kiệm/tuần/advisor (CEO phát biểu, Reuters 2024). • Có evaluation framework cho summarization, accuracy, coherence (OpenAI case study). | [OpenAI case study](https://openai.com/index/morgan-stanley/); [Reuters 2024](https://www.reuters.com/technology/morgan-stanley-ceo-says-ai-could-save-financial-advisers-10-15-hours-week-2024-06-10/); [CDO Magazine](https://www.cdomagazine.tech/aiml/98-of-morgan-stanley-wealth-management-advisors-use-its-ai-chatbot-with-improved-productivity-cao-explains-how) |
| Metric đó **chứng minh được gì**? | • **Adoption thật**: 98% FA dùng AI chatbot → vượt ngưỡng "công cụ chỉ có người thử". • **AI gắn vào workflow thật**: search tri thức, summarization, draft email — không phải chatbot chung. • **Productivity proxy có hướng tích cực**: tiết kiệm 10–15h/tuần là tín hiệu khá mạnh ở quy mô >16.000 người. • **Trust được thiết kế vào quy trình**: advisor luôn là người chỉnh sửa/gửi cuối → output AI có vòng kiểm tra. | Tổng hợp từ các nguồn trên |
| Metric đó **chưa chứng minh được gì**? | • **Không** chứng minh trực tiếp revenue/AUM per advisor tăng. • **Không** chứng minh client retention hoặc client outcome cải thiện. • Citation accuracy / NPS nội bộ: OpenAI nói có evals nhưng **không công bố số %** → không thể trích dẫn như "chứng minh chất lượng". • 10–15h/tuần là **CEO statement**, không phải audit độc lập. • 98% là số do CDO của Morgan Stanley nói, không có third-party verification. | OpenAI page chỉ mô tả framework, không công bố con số |
| Còn **thiếu metric** nào? | • **Override / edit rate**: % draft email bị FA sửa nhiều > X% trước khi gửi. • **Citation accuracy %** công khai (% câu trả lời có nguồn đúng). • **Outcome tài chính**: revenue uplift/advisor, AUM growth, lead conversion sau khi dùng AI. • **Client-side metric**: client satisfaction, retention, NPS sau khi FA dùng AI. • **Audit độc lập** về compliance khi AI tham gia soạn nội dung gửi khách. • **Time-saving thực tế (đo được)** thay vì self-report/CEO statement. | Suy luận từ khoảng trống trong public sources |
| **Bài học áp dụng vào dashboard NestAI** | 1. **Adoption cao + workflow rõ + human review** là combo của case thành công — NestAI cần đủ cả 3. 2. **Không tin một metric duy nhất**: Morgan Stanley có 98% adoption + 10–15h saved + citation accuracy → tổ hợp. NestAI cần tổ hợp D14 compliance × safety audit × clinical outcome proxy. 3. **CEO/PR statement ≠ audit**: phải phân biệt "công bố" và "đo được". 4. **Productivity proxy phải đi kèm quality proxy** (citation accuracy) — nếu không, "nhanh" có thể là "ẩu". 5. Mỗi metric nên có cột **"proves / does not prove"** để không rơi vào vanity metric. | Áp dụng trực tiếp vào Part B dashboard NestAI |

---

## 3. Nguồn tham khảo

| # | Nguồn | Dùng để chứng minh |
|---|---|---|
| 1 | [Forbes — Davenport (2023)](https://www.forbes.com/sites/tomdavenport/2023/03/20/how-morgan-stanley-is-training-gpt-to-help-financial-advisors/) | Quy mô >16.000 FA, >100.000 docs |
| 2 | [OpenAI case study](https://openai.com/index/morgan-stanley/) | Dùng GPT-4 + evaluation framework |
| 3 | [Morgan Stanley press release — Debrief](https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch) | Tính năng meeting notes/action items/draft email |
| 4 | [Reuters (2024)](https://www.reuters.com/technology/morgan-stanley-ceo-says-ai-could-save-financial-advisers-10-15-hours-week-2024-06-10/) | CEO statement: 10–15h/tuần |
| 5 | [CDO Magazine](https://www.cdomagazine.tech/aiml/98-of-morgan-stanley-wealth-management-advisors-use-its-ai-chatbot-with-improved-productivity-cao-explains-how) | 98% adoption (theo CDO) |

---

## 4. Một câu kết luận

Morgan Stanley là case tín hiệu tốt vì **adoption + workflow integration + human review** đi cùng nhau, nhưng các con số được công bố vẫn chủ yếu là **adoption + productivity proxy**, chưa phải **outcome tài chính** hay **audit chất lượng độc lập** — vì vậy dashboard NestAI phải đo cả lớp **outcome/quality**, không chỉ dừng ở "có người dùng" và "tiết kiệm thời gian".
