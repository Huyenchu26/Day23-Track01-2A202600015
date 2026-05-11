# Day 23 Lab — Product ROI Dashboard

**Chủ đề:** Đưa AI vào vận hành thực tế  
**Thời lượng:** 09:00-13:00  
**Hình thức:** cá nhân + nhóm 4-6 người  
**Sản phẩm chính:** một **Product ROI Dashboard** cho 1 sản phẩm AI cụ thể.

Mục tiêu của lab không phải là kể rằng "AI hay". Mục tiêu là thiết kế một dashboard giúp nhóm trả lời:

> Sản phẩm AI này có tạo giá trị thật không, hay chỉ có người dùng thử?

---

## 1. Cuối ngày cần nộp gì?

Mỗi học viên tạo **một repo GitHub cá nhân** và để tất cả bài nộp trong repo đó.

| File | Ai làm? | Deadline | Nội dung |
|---|---|---|---|
| `01-case-evidence-matrix.md` | Cá nhân | Trong Block 2 | Phân tích case được giao: metric chứng minh được gì, chưa chứng minh được gì |
| `02-case-comparison.md` | Nhóm, mỗi thành viên copy về repo cá nhân | Cuối Block 2 | So sánh case thành công / cảnh báo và rút bài học cho dashboard |
| `03-product-roi-dashboard.md` | Nhóm, mỗi thành viên copy về repo cá nhân | 13:00 | Dashboard Parts A-D sau khi red-team và sửa |
| `04-reflection.md` | Cá nhân | 24h sau lớp | 150-200 từ: 1 metric hoặc 1 giả định bạn sẽ sửa |

Cuối Block 5, mỗi học viên gửi link repo cá nhân lên Discord `#day23-submissions`.

---

## 2. Lịch làm bài

| Thời gian | Hoạt động | Kết quả |
|---|---|---|
| 09:00-10:00 | Lecture: AI adoption, ADKAR, Metrics Ladder, Measurement Trap, Gartner Lite, 25 tactics | Nắm framework để làm lab |
| 10:00-11:00 | Case study theo nhóm | Hoàn thành case matrix + case comparison |
| 11:00-12:00 | Build Product ROI Dashboard v1 | Có bản nháp Parts A-B-C |
| 12:00-12:30 | Red-team | Nhóm khác phản biện metric, rủi ro và decision logic |
| 12:30-13:00 | Revise + submit | Hoàn thành dashboard v2, decision memo và nộp repo |

---

## 3. Block 2 — Case Evidence Matrix và Case Comparison

Mục tiêu của Block 2 là học cách đọc metric từ case thật.

Mỗi cá nhân điền `01-case-evidence-matrix.md` cho case được giao. Sau đó nhóm tổng hợp thành `02-case-comparison.md`.

Case gợi ý:

| Nhóm case | Ví dụ |
|---|---|
| Thành công / tín hiệu tốt | Morgan Stanley, DWP/GDS, Stripe, Nansen |
| Cảnh báo / thất bại | Klarna, IBM Watson / MD Anderson, KPMG dashboard, JPMorgan dashboard |

Khi phân tích case, không chỉ kể chuyện. Hãy trả lời:

- AI được dùng trong workflow nào?
- Họ đo metric gì?
- Metric đó chứng minh được gì?
- Metric đó chưa chứng minh được gì?
- Còn thiếu metric nào?
- Bài học nào áp dụng được vào dashboard của nhóm?

Template: [`02-templates/00-case-evidence-matrix.md`](02-templates/00-case-evidence-matrix.md)

---

## 4. Block 3-5 — Product ROI Dashboard

Nhóm chọn **1 sản phẩm AI cụ thể** và **2-4 workflow chính**. Không chọn quá rộng kiểu "AI trong công ty" hoặc "dùng ChatGPT nói chung".

Trong bài này, **workflow** là một quy trình có điểm bắt đầu, người dùng rõ ràng, bước AI can thiệp, điểm con người kiểm tra và kết quả cuối có thể đo được.

| Scope còn mơ hồ | Workflow đo được |
|---|---|
| Dùng AI chăm sóc khách hàng | Phân loại ticket mới, gợi ý câu trả lời, agent kiểm tra rồi gửi, theo dõi khách có quay lại hỏi tiếp không |
| Dùng AI học tập | Upload tài liệu, tóm tắt nội dung, tạo quiz, gợi ý phần cần học lại |
| Dùng AI lập trình | Gợi ý code, tạo test, review PR, cập nhật tài liệu kỹ thuật |

Ví dụ scope tốt:

| Product | 2-4 workflow chính |
|---|---|
| AI chatbot cho chăm sóc khách hàng SME | Phân loại ticket, viết nháp phản hồi, agent review/send, theo dõi khách quay lại |
| AI learning assistant cho sinh viên đọc tài liệu | Upload PDF, tóm tắt, tạo quiz, gợi ý phần học tiếp theo |
| AI coding assistant cho team kỹ thuật | Gợi ý code, tạo test, review PR, cập nhật tài liệu |

### Part A — Adoption Context

Cần ghi rõ:

- Product là gì?
- Ai dùng product này?
- 2-4 workflow chính là gì?
- Trong từng workflow, AI làm phần nào?
- Con người kiểm tra ở đâu?
- Khi AI sai thì xử lý thế nào?
- Rào cản ADKAR chính là gì?
- 3 tactic nào sẽ dùng để tăng adoption?

Template: [`02-templates/01-part-a-adoption-context.md`](02-templates/01-part-a-adoption-context.md)

### Part B — ROI Dashboard

Dashboard dùng 8 cột:

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---|---|

Yêu cầu:

- Có metric ở cấp product và cấp workflow.
- Không chỉ đo login, prompt count, DAU/MAU hoặc số người mở tool.
- Phải có ít nhất một metric về quality, trust hoặc value.
- Mỗi metric quan trọng cần có baseline, target, data source và owner.

Template: [`02-templates/02-part-b-roi-dashboard.md`](02-templates/02-part-b-roi-dashboard.md)

### Part C — Dashboard Mock

Vẽ nhanh 4-6 ô dashboard. Không cần đẹp, nhưng phải thấy logic đo và hành động khi chỉ số đỏ.

Template: [`02-templates/03-part-c-dashboard-mock.md`](02-templates/03-part-c-dashboard-mock.md)

### Part D — Decision Memo

Trả lời ngắn 4 câu:

1. Nhóm đề xuất continue / pivot / kill?
2. Metric mạnh nhất là gì, vì sao?
3. Metric nào đã thay sau red-team?
4. Trước khi scale, nhóm phải làm gì?

Template: [`02-templates/04-part-d-decision-memo.md`](02-templates/04-part-d-decision-memo.md)

### Ví dụ mẫu — Klarna customer support AI

Dùng ví dụ này để hiểu deliverable cần trông như thế nào. Không copy nguyên số liệu nếu nhóm chọn product khác.

Case thật: [OpenAI công bố case Klarna](https://openai.com/index/klarna/) với các tín hiệu vận hành rất mạnh: AI assistant xử lý khoảng 2,3 triệu cuộc trò chuyện, khoảng hai phần ba tổng số chat, thời gian xử lý giảm từ 11 phút xuống dưới 2 phút, và được mô tả là tương đương khoảng 700 nhân sự toàn thời gian. Đến năm 2025, [Reuters đưa tin Klarna điều chỉnh trọng tâm](https://www.reuters.com/business/swedens-klarna-shifts-ai-focus-cost-cuts-growth-2025-09-10/), bổ sung lại yếu tố con người trong dịch vụ khách hàng.

Bài học cho dashboard: không dừng ở "AI xử lý nhiều chat". Volume và tốc độ là tín hiệu tốt, nhưng chưa đủ để chứng minh chất lượng, niềm tin và giá trị bền vững.

**Part A mẫu**

| Trường | Ví dụ điền |
|---|---|
| Product | AI customer support assistant |
| Người dùng chính | Khách hàng cần hỗ trợ + support agent |
| 2-4 workflow chính | Phân loại chat mới; trả lời case đơn giản; chuyển case phức tạp cho người thật; theo dõi khách quay lại hỏi tiếp |
| AI làm gì? | Nhận diện intent, trả lời câu hỏi thường gặp, gợi ý bước xử lý, tóm tắt case trước khi escalated |
| Con người kiểm tra ở đâu? | Case phức tạp, khiếu nại, hoàn tiền, tranh chấp, khách không hài lòng |
| Khi AI sai thì xử lý thế nào? | Escalate sang agent, ghi lý do lỗi, đưa vào QA sample, cập nhật rule hoặc prompt |
| Rào cản ADKAR chính | Ability + Reinforcement: agent cần biết khi nào tin AI, khi nào phải override |
| 3 tactic | Human-in-loop checklist; QA sample hằng tuần; dashboard cảnh báo khi repeat inquiry hoặc complaint tăng |

**Part B mẫu**

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---|---|
| Product / Activation | % eligible chats AI xử lý hoặc hỗ trợ | Case công bố: khoảng 2/3 chat | Duy trì ở nhóm case rủi ro thấp | Chat routing log | CX Ops Lead | Coverage cao có thể che case phức tạp bị xử lý kém | Tách metric theo độ phức tạp của case |
| Workflow / Productivity | Median resolution time | Case công bố: 11 phút | Dưới 2 phút nhưng quality không giảm | Ticket system | Support Ops Lead | Nhanh hơn nhưng có thể trả lời sai | Ghép với QA pass rate và repeat inquiry |
| Workflow / Quality | Repeat inquiry rate sau câu trả lời AI | Chưa đủ rõ trong public case | Không cao hơn human baseline | Ticket system | CX QA Lead | Không đo chỉ số này thì không biết khách có phải hỏi lại không | Theo dõi repeat trong 7 ngày sau ticket |
| Workflow / Trust | CSAT theo độ phức tạp của case | Chưa đủ rõ trong public case | Mỗi tier đạt hoặc vượt human baseline | Post-ticket survey | CX Lead | Average CSAT che mất nhóm case phức tạp | Tách simple / medium / complex case |
| Value | Cost per resolved ticket | Company-reported cost efficiency | Giảm chi phí chỉ khi complaint không tăng | Finance + ticket system | Finance BP | Cắt chi phí nhưng làm giảm trải nghiệm | Ghép với complaint rate và escalation success |

**Part C mẫu**

```text
[Product Coverage]        [Resolution Time]
2/3 eligible chats         <2 min, only valid if QA stable

[Quality]                 [Trust]
Repeat inquiry rate        CSAT by case complexity

[Value]                   [Decision]
Cost per resolved ticket   Continue routine cases, pivot complex cases to human-in-loop
```

**Part D mẫu**

Khuyến nghị: **continue with guardrails**. Tiếp tục dùng AI cho case đơn giản, nhưng pivot case phức tạp sang human-in-loop cho tới khi CSAT theo độ phức tạp, repeat inquiry và escalation success ổn định. Metric mạnh nhất không phải là "AI xử lý 2/3 chat", mà là tổ hợp: resolution time giảm, quality không giảm, trust không giảm.

---

## 5. Red-team

Red-team là vòng phản biện để giúp nhóm sửa dashboard trước khi nộp.

Mỗi nhóm phản biện nhóm khác theo một trong bốn vai:

| Vai | Câu hỏi chính |
|---|---|
| CFO | Metric này chứng minh tiền, chi phí, ROI hoặc giá trị thật ở đâu? |
| User | Dashboard hoặc tactic này có ép người dùng dùng AI sai cách không? |
| Risk | AI sai thì ai chịu trách nhiệm? Có quality check, audit trail, escalation không? |
| Workflow Owner | Data lấy từ đâu? Ai pull report? Ai xử lý khi chỉ số đỏ? |

Sau red-team, nhóm bị phản biện phải ghi:

- Red-team risk vào dashboard.
- Fix tương ứng.
- Ít nhất 2 thay đổi rõ từ v1 sang v2.

Template: [`02-templates/05-red-team-template.md`](02-templates/05-red-team-template.md)

---

## 6. Cách tính điểm

Day 23 = **100 điểm**.

| Hạng mục | Điểm |
|---|---:|
| Case Evidence Matrix | 15 |
| Case Comparison | 15 |
| Product ROI Dashboard v2 | 60 |
| Reflection cá nhân sau lớp | 10 |

Dashboard nhóm được chấm theo 6 điều kiện:

1. Scope rõ: 1 product cụ thể + 2-4 workflow chính.
2. Chẩn đoán đúng rào cản adoption.
3. Tactic gắn với đúng rào cản.
4. Metric đo được productivity, quality, trust hoặc value; không chỉ đo usage.
5. Baseline, target, data source và owner rõ.
6. Có red-team risk, Fix và ít nhất 2 thay đổi từ v1 sang v2.

Chi tiết rubric: [`../../assessment/day23-rubric-requirements.md`](../../assessment/day23-rubric-requirements.md)

---

## 7. Cách nộp bài

Tạo repo GitHub cá nhân:

| Trường | Yêu cầu |
|---|---|
| Tên repo | `Day23-Track01-<MãHọcViên>` |
| Visibility | Public |
| Branch | `main` |

Cấu trúc repo:

```text
Day23-Track01-<MãHọcViên>/
├── README.md
├── 01-case-evidence-matrix.md
├── 02-case-comparison.md
├── 03-product-roi-dashboard.md
├── 04-reflection.md
└── assets/
```

Lưu ý:

- File nộp dùng Markdown (`.md`).
- Mỗi thành viên copy file nhóm vào repo cá nhân.
- Discord chỉ dùng để gửi link repo, không nộp file trực tiếp.
- Repo phải public để đội chấm có thể truy cập.

---

## 8. Tài liệu cần mở

| File | Dùng để làm gì? |
|---|---|
| [`README.md`](README.md) | Tóm tắt nhanh buổi học và checklist nộp bài |
| [`01-worksheet.md`](01-worksheet.md) | Worksheet tổng hợp để làm dashboard |
| [`02-templates/00-case-evidence-matrix.md`](02-templates/00-case-evidence-matrix.md) | Template case matrix và case comparison |
| [`02-templates/01-part-a-adoption-context.md`](02-templates/01-part-a-adoption-context.md) | Template Part A |
| [`02-templates/02-part-b-roi-dashboard.md`](02-templates/02-part-b-roi-dashboard.md) | Template Part B |
| [`02-templates/03-part-c-dashboard-mock.md`](02-templates/03-part-c-dashboard-mock.md) | Template Part C |
| [`02-templates/04-part-d-decision-memo.md`](02-templates/04-part-d-decision-memo.md) | Template Part D |
| [`02-templates/05-red-team-template.md`](02-templates/05-red-team-template.md) | Template red-team |
| [`05-reference-document.md`](05-reference-document.md) | Tài liệu tham khảo đầy đủ |

---

## 9. Lỗi thường gặp

- Chọn scope quá rộng: "AI cho cả công ty".
- Chỉ đo usage: login, prompt count, DAU/MAU.
- Không có baseline hoặc target.
- Data source ghi quá chung chung.
- Owner ghi là "team" thay vì một role cụ thể.
- Productivity tăng nhưng không có quality hoặc trust đi kèm.
- Sau red-team nhưng dashboard v2 không sửa gì rõ ràng.

---

*Ngày 23 — VinUni A20 — AI Thực Chiến*
