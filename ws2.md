# Workshop 02 — Day 23: Nghiên Cứu Case Thành Công / Thất Bại

**Ngày:** 11/05/2026

## Thành viên nhóm

| STT | Họ và tên | Mã sinh viên |
|---|---|---|
| 1 | Chu Thị Ngọc Huyền | 2A202600015 |
| 2 | Nguyễn Thị Tuyết | 2A202600215 |
| 3 | Hứa Quang Linh | 2A202600466 |
| 4 | Dương Khoa Điềm | 2A202600366 |
| 5 | Hoàng Hiệp | 2A202600065 |

---

## 1. Hai case được chọn

| Loại case | Case được chọn | Lý do chọn |
|---|---|---|
| Case thành công | Morgan Stanley — AI @ Morgan Stanley Assistant / GPT-4 cho financial advisors | AI được gắn vào workflow thật của financial advisors: tra cứu tri thức nội bộ, chuẩn bị meeting, tóm tắt, tạo action items và draft email. |
| Case thất bại / cảnh báo | IBM Watson for Oncology / Oncology Expert Advisor tại MD Anderson Cancer Center | Dự án đầu tư lớn nhưng không chứng minh được clinical deployment thành công tại MD Anderson; là case cảnh báo về data readiness, workflow integration và outcome metric. |

---

## 2. Bảng kiểm chứng claim và nguồn

| Claim cần kiểm chứng | Sự thật & số liệu dùng được | Nguồn chứng minh |
|---|---|---|
| Morgan Stanley triển khai cho bao nhiêu financial advisors? | Morgan Stanley có hơn **16.000 financial advisors**. Bài Forbes của Tom Davenport viết rằng hệ thống GPT được huấn luyện để hỗ trợ hơn 16.000 financial advisors của Morgan Stanley. | Forbes / Tom Davenport: https://www.forbes.com/sites/tomdavenport/2023/03/20/how-morgan-stanley-is-training-gpt-to-help-financial-advisors/ |
| Có đúng là khoảng 100.000 internal documents không? | Có. Forbes ghi Morgan Stanley đã xác định nội dung trong hơn **100.000 tài liệu nội bộ** để financial advisors có thể hỏi. Đây là bằng chứng phù hợp cho claim “100.000 internal documents”. | Forbes / Tom Davenport: https://www.forbes.com/sites/tomdavenport/2023/03/20/how-morgan-stanley-is-training-gpt-to-help-financial-advisors/ |
| Morgan Stanley có dùng GPT-4 / OpenAI cho AI assistant không? | Có. OpenAI có case study chính thức về Morgan Stanley, nói Morgan Stanley dùng GPT-4 và xây hệ thống evaluation để kiểm tra summarization, accuracy, coherence. | OpenAI official: https://openai.com/index/morgan-stanley/ |
| Morgan Stanley có tính năng Debrief / meeting notes không? | Có. Morgan Stanley công bố **AI @ Morgan Stanley Debrief** có thể tạo meeting notes, action items, draft email, và lưu note vào Salesforce với sự đồng ý của client. Advisor vẫn là người chỉnh sửa/gửi theo quyết định của mình. | Morgan Stanley official: https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch |
| Adoption rate có thực sự đạt 98% không? | Có nguồn CDO Magazine nói **98% Morgan Stanley Wealth Management advisors use its AI chatbot**. Tuy nhiên, nên ghi rõ “theo CDO Magazine / phỏng vấn Atul Dalmia”, không ghi như audit độc lập. | CDO Magazine: https://www.cdomagazine.tech/aiml/98-of-morgan-stanley-wealth-management-advisors-use-its-ai-chatbot-with-improved-productivity-cao-explains-how |
| Time-saved 10–15 giờ/tuần có nguồn không? | Có. Reuters ghi CEO Ted Pick nói AI có thể giúp financial advisers tiết kiệm **10–15 giờ mỗi tuần**, đặc biệt qua việc transcribe và đưa meeting notes vào database. Đây là “potential saving / CEO statement”, không phải audit độc lập. | Reuters: https://www.reuters.com/technology/morgan-stanley-ceo-says-ai-could-save-financial-advisers-10-15-hours-week-2024-06-10/ |
| Citation accuracy / NPS có số liệu công khai không? | **Chưa thấy số liệu công khai cụ thể** về citation accuracy %, NPS hoặc CSAT nội bộ. Có thể nói OpenAI/Morgan Stanley có evaluation framework, nhưng không nên tự ghi số %. | OpenAI official chỉ nói có evals về accuracy/coherence, không công bố % cụ thể: https://openai.com/index/morgan-stanley/ |
| MD Anderson chi bao nhiêu cho IBM Watson? | JNCI ghi MD Anderson hợp tác với IBM năm 2012; sau **5 năm và 62 triệu USD**, MD Anderson để hợp đồng hết hạn trước khi Watson được dùng trên bệnh nhân thật. | JNCI / Oxford Academic: https://academic.oup.com/jnci/article/109/5/djx113/3847623 |
| Có đúng là Watson chưa được dùng trên bệnh nhân thật ở MD Anderson không? | Có. JNCI ghi rõ MD Anderson để hợp đồng IBM hết hạn **before anyone used Watson on actual patients**. | JNCI / Oxford Academic: https://academic.oup.com/jnci/article/109/5/djx113/3847623 |
| Có nguồn nào nói dự án bị hủy sau khoảng 62 triệu USD không? | Có. IEEE Spectrum viết dự án MD Anderson bị hủy năm 2016 sau khi chi khoảng **62 triệu USD**. | IEEE Spectrum: https://spectrum.ieee.org/how-ibm-watson-overpromised-and-underdelivered-on-ai-health-care |
| Nguyên nhân thất bại liên quan dữ liệu / EMR / workflow có nguồn không? | Có. IEEE Spectrum mô tả Oncology Expert Advisor dùng NLP để tóm tắt electronic health records và tìm database để đưa ra treatment recommendations. Đây là workflow khó vì phải xử lý dữ liệu y tế phức tạp, phi cấu trúc và tích hợp vào hệ thống bệnh viện. | IEEE Spectrum: https://spectrum.ieee.org/how-ibm-watson-overpromised-and-underdelivered-on-ai-health-care |
| Watson từng đưa ra khuyến nghị điều trị unsafe/incorrect có nguồn không? | Có. STAT News ghi internal IBM documents cho thấy Watson từng đưa ra nhiều khuyến nghị điều trị **“unsafe and incorrect”** khi IBM quảng bá sản phẩm cho bệnh viện và bác sĩ. Lưu ý: đây là về Watson for Oncology rộng hơn, không nên viết rằng lỗi này trực tiếp xảy ra trên bệnh nhân thật tại MD Anderson. | STAT News: https://www.statnews.com/2018/07/25/ibm-watson-recommended-unsafe-incorrect-treatments/ |

---

## 3. Bảng so sánh 2 case

| Trường | Case thành công — Morgan Stanley AI Assistant | Case thất bại / cảnh báo — IBM Watson / MD Anderson | Nguồn đính kèm |
|---|---|---|---|
| Case | Morgan Stanley hợp tác với OpenAI để xây AI assistant hỗ trợ financial advisors tìm kiếm, tổng hợp thông tin và chuẩn bị công việc tư vấn khách hàng. | MD Anderson hợp tác với IBM Watson để phát triển Oncology Expert Advisor, hệ thống hỗ trợ bác sĩ ung thư bằng cách đọc hồ sơ y tế, tóm tắt dữ liệu bệnh nhân và tìm trong database để đề xuất hướng điều trị. | OpenAI: https://openai.com/index/morgan-stanley/ <br> JNCI: https://academic.oup.com/jnci/article/109/5/djx113/3847623 |
| AI được dùng trong workflow nào? | (1) Advisor đặt câu hỏi nghiệp vụ. <br> (2) AI tìm thông tin từ kho tri thức nội bộ. <br> (3) AI hỗ trợ summarization, meeting notes, action items, draft email. <br> (4) Advisor kiểm tra/chỉnh sửa trước khi dùng với khách hàng. | (1) Hệ thống lấy dữ liệu hồ sơ bệnh nhân. <br> (2) Watson dùng NLP để tóm tắt EHR và tìm database. <br> (3) Output hướng tới treatment recommendations. <br> (4) Dự án không đi tới sử dụng thật trên bệnh nhân tại MD Anderson trước khi bị dừng. | Morgan Stanley Debrief: https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch <br> IEEE Spectrum: https://spectrum.ieee.org/how-ibm-watson-overpromised-and-underdelivered-on-ai-health-care |
| Họ công bố / được ghi nhận metric gì? | Có các số liệu công khai: hơn 16.000 advisors, hơn 100.000 tài liệu nội bộ, potential saving 10–15 giờ/tuần cho financial advisers, và nguồn CDO Magazine nói 98% advisors dùng AI chatbot. | Có các số liệu công khai: dự án chi khoảng 62 triệu USD và bị hủy/dừng trước khi chứng minh deployment thành công trên bệnh nhân thật tại MD Anderson. | Forbes: https://www.forbes.com/sites/tomdavenport/2023/03/20/how-morgan-stanley-is-training-gpt-to-help-financial-advisors/ <br> Reuters: https://www.reuters.com/technology/morgan-stanley-ceo-says-ai-could-save-financial-advisers-10-15-hours-week-2024-06-10/ <br> CDO Magazine: https://www.cdomagazine.tech/aiml/98-of-morgan-stanley-wealth-management-advisors-use-its-ai-chatbot-with-improved-productivity-cao-explains-how <br> JNCI: https://academic.oup.com/jnci/article/109/5/djx113/3847623 |
| Metric đó chứng minh được gì? | Chứng minh AI được gắn vào workflow thật của advisor và có tín hiệu productivity rõ hơn usage thuần: tìm tri thức nhanh hơn, tóm tắt meeting, tạo action items, draft email. | Chứng minh dự án có đầu tư lớn nhưng không chuyển hóa thành clinical deployment thành công tại MD Anderson. Đây là dấu hiệu rõ của gap giữa demo/kỳ vọng và triển khai workflow thật. | Reuters: https://www.reuters.com/technology/morgan-stanley-ceo-says-ai-could-save-financial-advisers-10-15-hours-week-2024-06-10/ <br> JNCI: https://academic.oup.com/jnci/article/109/5/djx113/3847623 |
| Metric đó chưa chứng minh được gì? | Chưa chứng minh trực tiếp revenue tăng, AUM/advisor tăng, client retention tăng hoặc client outcome tốt hơn. Chưa thấy số liệu công khai chắc về citation accuracy %, NPS nội bộ hoặc audit độc lập. | Chưa chứng minh Watson cải thiện survival rate, response rate, safety outcome hoặc ROI tài chính. Chưa có bằng chứng adoption thành công bởi bác sĩ trong workflow thật tại MD Anderson. | Các nguồn công khai hiện có không cung cấp đủ các outcome này; không tự suy diễn. |
| Thiếu metric nào? | Revenue uplift/advisor; client retention; advisor override rate; % câu trả lời/draft bị sửa hoặc bỏ; audit độc lập về compliance và accuracy; client satisfaction. | Doctor acceptance rate; override/disagreement rate; clinical outcome; safety incident rate; data readiness score; EMR integration success rate; cost per usable recommendation. | Suy luận từ khoảng trống metric trong nguồn public; dùng như “missing metrics”, không phải dữ liệu đã đo. |
| Bài học cho dashboard nhóm | Dashboard phải đo đủ 3 lớp: adoption, productivity, trust/quality. Với AI hỗ trợ tri thức, phải đo AI có giúp người dùng tìm thông tin nhanh hơn không, output có kiểm chứng được không, và người dùng có tiếp tục dùng trong workflow thật không. | Không được dừng ở input metric như ngân sách, số case test, số bác sĩ được training hoặc số recommendation được tạo. Với workflow rủi ro cao, phải đo outcome, quality, override, safety và readiness dữ liệu ngay từ v1. | Bài học rút ra từ đối chiếu hai case. |

---

## 4. Bài học rút ra cho dashboard nhóm

| Bài học | Morgan Stanley cho thấy gì? | IBM Watson / MD Anderson cảnh báo gì? | Áp dụng vào dashboard nhóm |
|---|---|---|---|
| Không đo bằng usage thuần | AI có giá trị hơn khi được đặt vào workflow cụ thể của advisor: tìm tài liệu, tóm tắt meeting, tạo action items, draft email. | Dự án lớn, nhiều chi phí và nhiều kỳ vọng vẫn có thể thất bại nếu không chứng minh được outcome thật. | Không kết luận thành công chỉ bằng số người dùng AI, số prompt hoặc số output. |
| Phải đo workflow outcome | Morgan Stanley đo/nhấn mạnh productivity proxy như tiết kiệm thời gian và giảm việc thủ công trong meeting notes. | Watson không chứng minh được deployment thật trên bệnh nhân tại MD Anderson. | Đo workflow cycle time, output acceptance rate, rework rate, cost per usable output. |
| Trust cần được thiết kế vào workflow | Advisor vẫn là người kiểm tra/chỉnh sửa trước khi gửi cho khách hàng; Debrief tạo draft email để advisor edit và send at their discretion. | Watson nằm trong workflow y tế rủi ro cao; nếu recommendation sai có thể gây hậu quả nghiêm trọng. | Cần human review point, override rate, quality flag rate, safety/trust metric. |
| Data readiness là điều kiện bật đèn xanh | Morgan Stanley dùng kho tri thức nội bộ tương đối rõ phạm vi: tài liệu nội bộ và research documents. | Watson phải xử lý hồ sơ y tế phức tạp, dữ liệu phi cấu trúc và tích hợp clinical workflow khó. | Trước khi đo ROI, dashboard cần kiểm tra data source, data quality, context completeness. |
| Metric phải nói rõ “chứng minh gì / chưa chứng minh gì” | 10–15 giờ/tuần là productivity proxy, nhưng chưa chứng minh revenue hoặc client outcome. | 62 triệu USD chi phí chỉ chứng minh đầu tư lớn, không chứng minh value. | Mỗi metric cần có cột “proves / does not prove” để tránh vanity metric. |

---

## 5. Áp dụng vào case của nhóm  
### AI trả lời email khách hàng — từ WS1

| Nguồn học | Metric / yếu tố cần thêm vào dashboard | Cách áp dụng vào case AI trả lời email khách hàng |
|---|---|---|
| Từ Morgan Stanley | Citation / source rate | Mỗi nội dung AI gợi ý trả lời email cần có căn cứ từ CRM, lịch sử khách hàng, chính sách, tài liệu sản phẩm hoặc email trước đó. |
| Từ Morgan Stanley | Time-saved per email | Đo thời gian trung bình CS agent xử lý một email trước và sau khi có AI hỗ trợ. |
| Từ Morgan Stanley | CS agent satisfaction / internal NPS | Đo mức độ nhân viên CS cảm thấy AI thật sự giúp việc hay chỉ tạo thêm việc kiểm tra. |
| Từ Watson | Override rate | Đo % bản nháp AI bị CS agent bỏ hoàn toàn hoặc sửa quá nhiều trước khi gửi. |
| Từ Watson | QA rework rate | Đo % email có AI hỗ trợ nhưng bị QA flag hoặc yêu cầu sửa lại. |
| Từ Watson | Escalation rate khi AI sai | Đo % trường hợp AI gợi ý sai khiến email phải escalated lên supervisor hoặc team chuyên môn. |
| Từ Watson | Data-readiness check | Kiểm tra context đầu vào có đủ không: CRM, lịch sử khách hàng, chính sách hiện hành, trạng thái đơn hàng, lịch sử khiếu nại. |

---

## 6. Vanity metric cần bỏ hoặc không dùng một mình

| Vanity metric | Vì sao chưa đủ? | Metric nên đi kèm |
|---|---|---|
| Số email có AI hỗ trợ | Chỉ chứng minh AI có tham gia, chưa chứng minh email tốt hơn | % email gửi đi không bị QA flag |
| Số người dùng AI | Chỉ chứng minh có người mở tool | Retention + workflow completion |
| Số prompt | Có thể là dấu hiệu bị kẹt, không phải năng suất | Prompt-to-acceptance ratio |
| Số output AI tạo ra | Output nhiều chưa chắc dùng được | Output acceptance rate + rework rate |
| Số case test | Test nhiều chưa chứng minh outcome | Outcome metric + quality audit |
| Ngân sách đã chi | Chi nhiều không đồng nghĩa có ROI | Cost per usable output |
| Thời gian dùng AI | Dùng lâu có thể là hiệu quả thấp | Time saved per workflow |

---

## 7. Kết luận

| Kết luận chính | Ý nghĩa cho dashboard |
|---|---|
| AI adoption không thành công chỉ vì có triển khai AI. | Dashboard không được dừng ở login, prompt count, output count. |
| AI phải được gắn vào workflow thật. | Mỗi metric phải gắn với một bước trong workflow trả lời email khách hàng. |
| Dữ liệu đầu vào phải đủ sẵn sàng. | Cần data-readiness check trước khi tính ROI. |
| Output phải có thể kiểm chứng. | Cần citation/source rate, human review point và QA flag. |
| Người dùng phải tin và tiếp tục dùng AI. | Cần retention, override rate và CS agent satisfaction. |
| ROI phải đo trên output dùng được. | Cần cost per usable email / cost per resolved email, không chỉ cost per generated draft. |