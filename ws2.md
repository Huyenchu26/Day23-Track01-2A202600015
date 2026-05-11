# Workshop 02 — Day 23: Nghiên Cứu Case Thành Công / Thất Bại

**Nhóm:** [tên nhóm]
**Sinh viên:** Chu Thị Ngọc Huyền (2A202600015)
**Ngày:** 11/05/2026

---

## 1. Hai case được chọn

- **Case thành công:** Morgan Stanley — AI @ Morgan Stanley Assistant (GPT-4) cho financial advisors.
- **Case thất bại / cảnh báo:** IBM Watson for Oncology tại MD Anderson Cancer Center.

---

## 2. Bảng so sánh case

| Trường | Case thành công — Morgan Stanley AI Assistant | Case thất bại / cảnh báo — IBM Watson / MD Anderson |
|---|---|---|
| **Case** | Morgan Stanley triển khai GPT-4 assistant cho ~16.000 financial advisor để tra cứu nội bộ knowledge base (hơn 100k research docs). | MD Anderson hợp tác IBM Watson for Oncology để gợi ý phác đồ điều trị ung thư cá nhân hoá. Dự án bị dừng năm 2017 sau khi chi ~$62M. |
| **AI được dùng trong workflow nào?** | (1) Advisor hỏi câu hỏi nghiệp vụ → AI tìm và trích dẫn tài liệu nội bộ. (2) Soạn nháp tóm tắt cho client meeting. (3) Tra cứu compliance / sản phẩm. Mỗi workflow đều có advisor là human-in-the-loop trước khi gửi cho khách. | (1) Bác sĩ nhập hồ sơ bệnh nhân → Watson gợi ý phác đồ. (2) Watson được train trên hồ sơ ảo / hypothetical cases thay vì hồ sơ thật. (3) Output là khuyến nghị điều trị, không có vòng human-review chuẩn hóa, không tích hợp được vào EMR thật. |
| **Họ đo metric gì?** | % advisor active hằng tuần (>98% team adopt), số câu hỏi/advisor/tuần, thời gian tìm tài liệu (giảm từ phút → giây), tỉ lệ trích dẫn nguồn chuẩn (citation accuracy), advisor satisfaction (NPS nội bộ), số meeting prep được rút ngắn. | Chủ yếu là metric quá trình: số case test, số phác đồ Watson đưa ra, số bác sĩ được training, ngân sách đã chi. Không có metric outcome lâm sàng công bố. |
| **Metric đó chứng minh được gì?** | Chứng minh: (a) advisor thực sự dùng (activation + retention), (b) AI tiết kiệm thời gian thật (productivity), (c) output có nguồn để verify (trust/quality), (d) người dùng tin và tiếp tục dùng (NPS + retention). | Chứng minh: đã có hoạt động và chi tiêu (input/effort). Cho thấy hệ thống có chạy về mặt kỹ thuật. |
| **Metric đó CHƯA chứng minh được gì?** | Chưa chứng minh trực tiếp ra doanh thu/AUM tăng hoặc client outcome (retention khách hàng, % deal close, revenue/advisor). “Citation accuracy” là proxy của trust, không bằng audit độc lập. | Chưa chứng minh giá trị lâm sàng: không có dữ liệu phác đồ Watson cải thiện survival, không có tỉ lệ bác sĩ accept gợi ý, không có safety/incident rate, không có ROI tài chính. Không trả lời được câu “bệnh nhân có sống lâu hơn không?”. |
| **Thiếu metric nào?** | – Outcome tài chính (AUM/advisor, client retention, revenue uplift). – Quality audit độc lập (% câu trả lời sai về compliance). – Override rate: advisor sửa/bỏ output của AI bao nhiêu %. | – Acceptance rate của bác sĩ. – Override / disagreement rate. – Outcome lâm sàng (survival, response rate, adverse event). – Data-readiness metric (Watson train trên dữ liệu nào, generalize ra bệnh nhân thật được không). – Integration metric (có chạy được trong EMR thật không). – Cost-to-value (chi phí/ca dùng được). |
| **Bài học cho dashboard của nhóm** | Đo cả 3 lớp: **adoption** (có dùng) + **productivity** (nhanh hơn) + **trust/quality** (có nguồn, có audit). Mỗi workflow phải có human-review point rõ. | Không được dừng ở **input metric** (đã chi, đã train, đã demo). Phải có **outcome + quality + override** ngay từ v1, và phải kiểm tra **readiness của dữ liệu** trước khi đếm “AI đã làm gì”. |

---

## 3. Bài học rút ra cho dashboard nhóm

1. **Không đo bằng usage thuần.** Active users / số prompt cao như Watson không cứu được dự án nếu không có outcome. Morgan Stanley đo usage *kèm* citation accuracy + time-saved → mới chứng minh được giá trị.
2. **Phải có 3 lớp tối thiểu cho mỗi workflow:** Adoption → Productivity/Quality → Trust (override/accept rate). Thiếu lớp Trust là thiếu cái Watson đã thiếu.
3. **Readiness của dữ liệu phải là điều kiện bật đèn xanh, không phải metric phụ.** Watson fail một phần vì train trên hypothetical cases. Dashboard nhóm cần một ô “data source + data quality check” trước khi tính ROI.
4. **Mỗi metric phải trả lời được câu “chứng minh cái gì, chưa chứng minh cái gì”.** Nếu một chỉ số không loại được giả thuyết “AI vẫn vô dụng”, thì nó là vanity metric và phải thay.

---

## 4. Áp dụng vào case của nhóm (AI trả lời email khách hàng — từ ws1)

- Từ Morgan Stanley: thêm **citation/source rate** + **time-saved per email** + **advisor (CS agent) NPS**.
- Từ Watson: thêm **override rate** (% nháp bị CS agent sửa nhiều), **QA rework rate**, **escalation rate khi AI sai**, và **data-readiness check** cho context của email (CRM, lịch sử khách).
- Vanity metric cần bỏ: “số email có AI hỗ trợ” một mình — phải đi kèm “% email gửi đi không bị QA flag”.
