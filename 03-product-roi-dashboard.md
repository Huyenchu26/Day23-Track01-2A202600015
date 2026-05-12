# Day 23 — Worksheet Product ROI Dashboard


## 0. Thông tin nhóm

| Trường | Trả lời |
|---|---|
| Nhóm | Nhóm 005 — NestAI |
| Người phụ trách | Chu Thị Ngọc Huyền|
| Product chọn phân tích | **NestAI** — App gợi ý thực đơn dinh dưỡng cá nhân hoá cho mẹ bầu Việt có bệnh lý thai kỳ (tiểu đường, thiếu máu) |
| Người dùng chính | Phụ nữ mang thai 22–35 tuổi, trimester 2–3, vừa được chẩn đoán tiểu đường thai kỳ hoặc thiếu máu thiếu sắt, có smartphone |
| Link repo / file nộp cuối | `Day23-Track01-2A202600015/03-product-roi-dashboard.md` |

---

## 1. Case Comparison

Tóm tắt bài học từ case study để dùng cho dashboard.

| Trường | Case thành công / tín hiệu tốt — **Morgan Stanley AI Assistant** | Case cảnh báo / thất bại — **IBM Watson for Oncology @ MD Anderson** |
|---|---|---|
| Case | GPT-4 assistant cho ~16.000 financial advisor truy cập ~100k research docs nội bộ. | Watson được dùng để gợi ý phác đồ điều trị ung thư cá nhân hoá; dự án bị dừng năm 2017 sau khi chi ~$62M. |
| AI được dùng trong workflow nào? | Advisor hỏi nghiệp vụ → AI trích dẫn tài liệu nội bộ; soạn nháp tóm tắt client meeting; tra cứu compliance/sản phẩm. Advisor là human-in-the-loop trước khi gửi khách. | Bác sĩ nhập hồ sơ bệnh nhân → Watson đề xuất phác đồ. Train trên hypothetical cases, không có vòng human-review chuẩn hoá, không integrate vào EMR thật. |
| Người dùng chính là ai? | Financial advisor (nội bộ) phục vụ khách hàng wealth management. | Bác sĩ ung thư tại MD Anderson; bệnh nhân là người chịu hậu quả cuối cùng. |
| Họ đo metric gì? | % advisor active hằng tuần (>98%), số câu hỏi/advisor/tuần, thời gian tìm tài liệu (phút → giây), citation accuracy, advisor NPS. | Metric quá trình: số case test, số phác đồ Watson đưa ra, số bác sĩ training, ngân sách đã chi. Không có metric outcome lâm sàng công bố. |
| Metric đó chứng minh được gì? | Advisor thực sự dùng (activation + retention), AI tiết kiệm thời gian (productivity), output có nguồn để verify (trust), người dùng tin và tiếp tục dùng (NPS). | Đã có hoạt động và chi tiêu (input/effort). Hệ thống chạy được về mặt kỹ thuật. |
| Metric đó chưa chứng minh được gì? | Chưa chứng minh trực tiếp doanh thu/AUM tăng hay client retention; citation accuracy là proxy của trust, không bằng audit độc lập. | Không chứng minh giá trị lâm sàng: không có survival rate, accept rate của bác sĩ, safety/incident rate, ROI tài chính. |
| Thiếu metric nào? | Outcome tài chính (AUM/advisor, revenue uplift), audit độc lập về compliance, override rate (advisor sửa output AI bao nhiêu %). | Acceptance/override rate của bác sĩ, outcome lâm sàng, data-readiness, integration metric, cost-to-value. |
| Bài học cho dashboard nhóm | Đo đủ 3 lớp: **adoption + productivity + trust/quality**. Mỗi workflow phải có human-review point rõ. | Không dừng ở **input metric** (đã chi, đã train, đã demo). Phải có **outcome + quality + override** ngay từ v1; kiểm tra **readiness dữ liệu** trước khi đếm "AI đã làm gì". |

**Bài học  sẽ áp dụng vào dashboard:**

```markdown
1. Không đo bằng usage thuần — login, prompt count, DAU/MAU không chứng minh được NestAI có giúp mẹ bầu ăn đúng hơn.
2. Mỗi workflow của NestAI phải có ít nhất 3 lớp: Adoption → Productivity/Quality → Trust (compliance + override rate).
3. Readiness của dữ liệu (nutrition DB Việt + food recognition model) là điều kiện bật đèn xanh, không phải metric phụ — tránh lặp lại lỗi Watson train trên hypothetical cases.
4. Mỗi metric phải trả lời được "chứng minh được gì / chưa chứng minh được gì". Nếu không loại được giả thuyết "NestAI vẫn vô dụng cho mẹ bầu", đó là vanity metric.
5. Phải có safety guardrail rõ (giống Morgan Stanley có citation): khi confidence < 60%, fallback sang hotline bác sĩ / rule-based menu.
```

---

## 2. Part A — Adoption Context

| Trường | Trả lời |
|---|---|
| Product | **NestAI** — App iOS gợi ý thực đơn Việt cá nhân hoá theo bệnh lý thai kỳ + meal logging bằng ảnh. |
| Người dùng chính | Mẹ bầu lần đầu, 22–35 tuổi, trimester 2–3, có chẩn đoán tiểu đường thai kỳ (GDM) hoặc thiếu máu thiếu sắt (IDA), sống ở TP.HCM / Hà Nội. |
| Bối cảnh sử dụng | Mỗi sáng quyết định 3 bữa ăn trong ngày + ghi nhận bữa giữa ngày khi ăn ngoài / ăn quán. Người dùng vừa lo lắng (anxiety post-diagnosis) vừa thiếu thời gian. |
| Mục tiêu kinh doanh / học tập / vận hành | Đạt **D14 menu compliance ≥ 50%** và **D30 retention ≥ 35%** trong cohort GDM/IDA tại 2 thành phố, làm bằng chứng để gọi seed round và mở rộng partnership với phòng khám sản. |
| Rào cản ADKAR chính | **Knowledge + Ability**: mẹ bầu *muốn* (Desire cao do lo cho con) và *biết có app* (Awareness ok khi qua bác sĩ giới thiệu), nhưng (a) chưa biết menu AI có an toàn cho bệnh lý của mình không (Knowledge), và (b) chưa quen thao tác chụp ảnh + swap món (Ability). **Reinforcement** là rào cản phụ — không có ai nhắc lại tuần 2, dễ bỏ. |

### 2-4 workflow chính

| # | Workflow | AI làm gì? | Con người kiểm tra ở đâu? | Khi AI sai thì xử lý thế nào? |
|---|---|---|---|---|
| 1 | **Onboarding & Profile** — mẹ bầu nhập trimester, bệnh lý kèm, vùng miền, dị ứng | Chuẩn hoá input, gợi ý profile preset theo bệnh lý, generate menu mẫu ngày 1 để demo giá trị | Mẹ bầu xác nhận bệnh lý + trimester; dietitian QA review 10% profile preset mỗi tuần | Nếu bệnh lý ngoài 3 loại đã có protocol → fallback sang rule-based "thực đơn an toàn chung" + prompt liên hệ dietitian |
| 2 | **Menu Generation** — sinh thực đơn cả ngày theo bệnh lý × trimester × vùng miền | GPT-4o sinh 3 bữa + 2 snack, có chỉ số GI/sắt/folate; cho phép swap món | Mẹ bầu duyệt menu mỗi sáng; dietitian audit 5% menu/tuần đối chiếu phác đồ Bộ Y tế VN | Nếu menu chứa món không có trong nutrition DB → block + fallback sang menu template đã pre-approved; ghi vào QA log để retrain |
| 3 | **Photo Meal Logging** — chụp ảnh bữa ăn → ước tính kcal + vi chất | Vision API nhận diện món; nếu confidence < 60% hỏi lại tên món; tính sắt/folate so với target tuần | Mẹ bầu xác nhận tên món + size estimate; user-corrected labels được dietitian verify trước khi đưa vào training set | Hiển thị badge "Ước tính (~)" thay vì số tuyệt đối; nếu sai 3 lần liên tiếp gợi ý nhập thủ công |
| 4 | **Safety Escalation** — phát hiện triệu chứng bất thường hoặc swap thất bại nhiều lần | Phân loại keyword nguy hiểm (đau bụng, ra máu, đường huyết cao) trong feedback/chat; flag case bất thường | Care coordinator (dietitian on-call) đọc flag trong vòng 4h; với keyword đỏ → hotline bác sĩ ngay | Nếu AI bỏ sót keyword đỏ → SLA review hằng tuần; tăng recall của classifier; thêm rule-based safety net keyword |

### 3 tactic tăng adoption

| Tactic | Nhắm vào rào cản nào? | Áp dụng cho workflow nào? | Người phụ trách |
|---|---|---|---|
| 1. "Bác sĩ giới thiệu" — gắn QR code app vào tờ kê đơn của 5 phòng khám sản đối tác; bác sĩ giải thích NestAI an toàn cho bệnh lý → tăng trust ban đầu | Knowledge (mẹ bầu không biết menu AI có an toàn cho bệnh lý không) | Workflow 1 (Onboarding) | Clinical Partnership Lead |
| 2. Onboarding 3-bước có demo menu ngày 1 + nhắc swap món lần đầu trong app; tuần đầu có dietitian chat support trong giờ hành chính | Ability (chưa quen thao tác swap + chụp ảnh) | Workflow 1, 2, 3 | Product Lead |
| 3. Tuần 2 push notification cá nhân ("Tuần này thai 27 tuần, target sắt 27mg/ngày, bạn đã đạt 60%"); kèm milestone badge mỗi 7 ngày compliance | Reinforcement (rớt sau tuần 1) | Workflow 2, 3 | Growth / Lifecycle Lead |

---

## 3. Part B — ROI Dashboard

### B.1 Metric toàn product

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---|---|
| Activation | % user hoàn tất onboarding + nhận menu ngày 1 trong vòng 24h | 0% (chưa có) | ≥ 70% | App analytics (Amplitude) | Product Lead | Mẹ bầu nhập profile giả/qua loa để xem nhanh menu → menu không thực sự cá nhân hoá | Thêm dietitian QA sample 10% profile/tuần; flag profile thiếu trường bệnh lý / trimester |
| Engagement / Retention | D30 retention trong cohort GDM/IDA (đã đạt compliance D14 ≥ 50%) | Tự xây — chưa có baseline ngành cho VN | ≥ 35% | App analytics + compliance self-report | Growth Lead | Retention cao có thể chỉ là người mở app xem menu, không ăn thật | Ghép retention với compliance D14 + photo log frequency ≥ 3/tuần |
| Trust / Quality / Value | **Menu safety audit pass rate** — % menu sample được dietitian audit không chứa violation phác đồ Bộ Y tế VN (GI > threshold cho GDM, sắt < min cho IDA…) | Tự xây — chưa có | ≥ 98% pass; 0 violation nghiêm trọng | Dietitian audit log (audit 5% menu/tuần, ngẫu nhiên) | Clinical Lead (dietitian partner) | Audit chỉ 5% có thể bỏ sót edge case; dietitian thiên về vote pass vì là partner | Tăng audit lên 10% cho cohort GDM (cao rủi ro); blind review — dietitian không thấy nguồn menu là AI hay human |

### B.2 Metric theo workflow

#### Workflow 1 — Onboarding & Profile

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---|---|
| Activation | % user hoàn tất 100% trường bắt buộc (trimester, bệnh lý, vùng miền, dị ứng) | 0% | ≥ 80% | Amplitude funnel | Product Lead | User skip trường dị ứng → menu nguy hiểm | Block menu generation nếu thiếu trường dị ứng + bệnh lý |
| Engagement | % user quay lại đặt câu hỏi onboarding (chat support) trong tuần 1 | – | 20–30% (signal chứ không "càng cao càng tốt") | In-app chat log | CX Lead | Quá thấp = mẹ bầu bỏ qua không hiểu; quá cao = onboarding rối | Định nghĩa healthy band; flag ngoài band |
| Productivity | Thời gian trung bình hoàn tất onboarding | Form giấy ở phòng khám: ~12 phút | ≤ 4 phút | App analytics | Product Lead | Rút ngắn quá → user không đọc kỹ disclaimer y tế | Buộc check disclaimer + giữ 1 step xác nhận bệnh lý |
| Quality | % profile được dietitian audit "đúng/an toàn để generate menu" | – | ≥ 95% | Dietitian audit log | Clinical Lead | Audit thiên về pass | Blind review, audit có ghi nguyên nhân fail |
| Trust | % user trả lời "Tôi tin app hiểu đúng tình trạng của tôi" ≥ 4/5 sau onboarding | – | ≥ 70% | In-app survey (1 câu) | Product Lead | User trả lời lịch sự dù chưa thực sự tin | Ghép với behavioral signal: có generate menu ngày 1 không |
| Value | Cost per activated user (CAC qua kênh phòng khám) | – | ≤ 80k VND/user (target để LTV/CAC ≥ 3 ở tháng 12) | Finance + attribution | Finance BP | Tối ưu CAC mà bỏ kênh phòng khám có trust cao | Tách CAC theo kênh, không chỉ blended |

#### Workflow 2 — Menu Generation

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---|---|
| Activation | % user xem menu ngày đầu trong vòng 24h sau onboarding | 0% | ≥ 75% | App analytics | Product Lead | Xem menu ≠ ăn theo menu | Ghép với compliance self-report D3 |
| Engagement | Số ngày/tuần user mở menu (trong cohort D14) | – | ≥ 5 ngày/tuần | App analytics | Growth Lead | Mở app không bằng nấu/ăn theo | Ghép với photo log + self-report compliance |
| Productivity | Thời gian từ "mở app" → "có menu cả ngày" | Tự tra Google: 15–30 phút | ≤ 30 giây (gen) + ≤ 2 phút (review + swap nếu cần) | Server log | AI Eng Lead | Generate nhanh nhưng output rỗng | Buộc menu phải đủ 3 bữa + 2 snack + ghi nguồn nutrition |
| **Quality** | **Menu compliance D14** — % user báo "đã ăn đúng/gần đúng menu ≥ 7/14 ngày" | – | **≥ 50%** | Self-report survey D14 + photo log triangulation | Product Lead | Self-report bias (mẹ bầu nói "có ăn" vì ngại) | Triangulate với photo log ≥ 3/tuần; chỉ tính compliance khi có ≥ 1 signal khách quan |
| **Trust** | **Swap rate per menu** + lý do swap | – | Healthy band 1–3 món/menu; <1 = ép buộc, >3 = menu kém | App analytics + reason tag | Product Lead | Swap thấp ≠ tốt, có thể user bỏ cuộc | Phân biệt "swap rồi ăn" vs "không ăn cả menu" |
| **Value** | **Clinical outcome proxy** — % user GDM tự báo cáo đường huyết đói trong target zone (≤ 5.3 mmol/L) sau 4 tuần | – | ≥ 50% (tham chiếu phác đồ Bộ Y tế) | Weekly self-report + (long-term) integration phòng khám | Clinical Lead | Self-report đường huyết không thay máy đo HbA1c | V2 partnership phòng khám lấy HbA1c thật từ tuần 12 |

#### Workflow 3 — Photo Meal Logging

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---:|---|
| Activation | % user log ≥ 1 ảnh trong 7 ngày đầu | 0% | ≥ 40% | App analytics | Product Lead | Log 1 ảnh rồi bỏ | Đo cả frequency D14 |
| Engagement | % user log ≥ 3 ảnh/tuần trong 7 ngày đầu | – | ≥ 30% | App analytics | Growth Lead | User log ảnh không ăn (ảnh menu nhà hàng) | Detect duplicate / stock photo; chỉ count ảnh user vừa chụp |
| Productivity | Thời gian từ "mở camera" → "có kết quả kcal/vi chất" | Nhập thủ công: 3–5 phút | ≤ 15 giây | Server log | AI Eng Lead | Nhanh nhưng sai → user mất niềm tin | Ghép với accuracy + correction rate |
| Quality | Food recognition accuracy (top-1) trên 100 món Việt phổ biến | Vision API zero-shot: ~45% | ≥ 75% top-1; ≥ 90% top-3 | Internal eval set + user correction log | AI Eng Lead | Accuracy cao trên test set không sống ngoài đời | Hằng tháng đánh giá lại với user-corrected labels |
| Trust | **Correction rate** — % ảnh user phải sửa tên món | – | ≤ 25% (giảm dần theo quý) | App correction log | AI Eng Lead | Correction thấp do user lười sửa, không phải AI đúng | Sample QA: dietitian double-check 5% ảnh + correction |
| Value | % user thay đổi bữa tối dựa trên feedback vi chất buổi trưa | – | ≥ 25% (proxy cho behavior change) | App analytics (event "swap dinner after lunch log") | Product Lead | Hành vi không bền — chỉ thay đổi vì hứng thú ban đầu | Đo lại ở W4 và W8 để confirm |

#### Workflow 4 — Safety Escalation

| Layer | Metric | Baseline | Target | Data source | Owner | Red-team risk | Fix |
|---|---|---:|---:|---|---|---:|---|
| Activation | % keyword đỏ (đau bụng, ra máu, đường huyết > 10) được detect bởi classifier | – | ≥ 95% recall trên eval set | Eval set 200 ca giả lập + real flag | AI Eng Lead | Recall cao kèm precision thấp → spam dietitian | Báo cáo cả precision + recall, target precision ≥ 70% |
| Engagement | % user nhận escalation đã thực sự gọi hotline / tới khám | – | ≥ 60% trong 24h | Care coordinator follow-up log | Clinical Lead | Khó verify; user có thể tự đến chỗ khác | Hỏi xác nhận sau 48h |
| Productivity | Thời gian từ flag → care coordinator phản hồi | Không có quy trình hiện tại | ≤ 4h trong giờ hành chính, ≤ 12h ngoài giờ | Care log | Clinical Lead | Tăng tốc bằng cách giảm chất lượng review | Đo cả response time + override rate |
| Quality | False negative rate (case bị miss) | – | ≤ 1% với keyword đỏ | Weekly QA review của dietitian | Clinical Lead | Khó biết bị miss vì user không quay lại | Cross-check với complaint log + post-mortem nếu có sự cố |
| **Trust** | Số sự cố y tế nghiêm trọng / 1.000 user/tháng | – | **0** (hard gate) | Incident log | Clinical Lead | Có thể không được báo cáo | Đường dây ẩn danh + làm việc với phòng khám đối tác |
| Value | Cost per escalation handled vs. cost per ER visit tránh được | – | Track only — chưa target | Finance + clinical log | Finance BP | Không nên scale escalation để tiết kiệm tiền ER | Đây là metric *track*, không phải *optimize* |

---

## 4. Part C — Dashboard Mock

```text
┌──────────────────────────────────┐ ┌──────────────────────────────────┐
│ PRODUCT HEALTH                   │ │ WORKFLOW 2 — MENU GENERATION     │
│ Metric: D14 Menu Compliance      │ │ Metric: Compliance D14 + Swap    │
│ Current: – Target: ≥ 50%         │ │ Current: – Target: ≥ 50% / 1–3   │
│ Status: Green / Amber / Red      │ │ Status: Green / Amber / Red      │
│ Action if red: kiểm dietitian    │ │ Action if red: audit menu sample │
│ audit + phỏng vấn 10 mẹ bầu rớt  │ │ + retrain prompt với failure log │
└──────────────────────────────────┘ └──────────────────────────────────┘

┌──────────────────────────────────┐ ┌──────────────────────────────────┐
│ WORKFLOW 3 — PHOTO LOGGING       │ │ QUALITY / TRUST                  │
│ Metric: % user ≥ 3 ảnh/tuần      │ │ Metric: Menu safety audit pass   │
│ Current: – Target: ≥ 30%         │ │ Current: – Target: ≥ 98%         │
│ Status: Green / Amber / Red      │ │ Status: Green / Amber / Red      │
│ Action if red: rút gọn flow chụp │ │ Action if red: PAUSE menu gen    │
│ + tăng correction quality        │ │ cho bệnh lý đang fail; rerun QA  │
└──────────────────────────────────┘ └──────────────────────────────────┘

┌──────────────────────────────────┐ ┌──────────────────────────────────┐
│ VALUE — CLINICAL OUTCOME PROXY   │ │ DECISION                         │
│ Metric: % GDM user đường huyết   │ │ Continue / Pivot / Kill: TBD     │
│ trong target zone sau 4 tuần     │ │ Metric mạnh nhất: D14 compliance │
│ Current: – Target: ≥ 50%         │ │ × safety audit pass × outcome    │
│ Status: Green / Amber / Red      │ │ proxy (đường huyết target zone)  │
│ Action if red: clinical review;  │ │ Before scale: ký MOU 5 phòng     │
│ không scale tới bệnh lý mới      │ │ khám + 0 sự cố y tế / 3 tháng    │
└──────────────────────────────────┘ └──────────────────────────────────┘

┌──────────────────────────────────┐
│ SAFETY GATE (HARD)               │
│ Metric: Sự cố y tế nghiêm trọng  │
│ /1.000 user/tháng                │
│ Current: – Target: 0             │
│ Status: Green / RED ONLY         │
│ Action if red: STOP onboarding   │
│ user mới, full incident review   │
└──────────────────────────────────┘
```

---

## 5. Part D — Decision Memo

```markdown
# Decision Memo — NestAI

1. Nhóm khuyến nghị: **continue with guardrails** (tiếp tục validate MVP trong cohort GDM/IDA tại TP.HCM/Hà Nội với 200–500 mẹ bầu trong 8–12 tuần, KHÔNG mở rộng sang bệnh lý khác hay general pregnancy cho tới khi gate được mở).

2. Metric mạnh nhất để bảo vệ quyết định là:
   **Tổ hợp 3 metric — không phải 1 metric đơn lẻ**:
   (a) **D14 menu compliance ≥ 50%** (chứng minh mẹ bầu thực sự ăn theo menu, không chỉ xem),
   (b) **Menu safety audit pass rate ≥ 98%** (chứng minh AI không vi phạm phác đồ Bộ Y tế),
   (c) **Clinical outcome proxy** — % GDM user trong target zone đường huyết đói sau 4 tuần ≥ 50% (chứng minh có giá trị y tế thật, không chỉ "app dễ dùng").
   Tránh dùng số lượt tải, prompt count, DAU/MAU làm metric chính — chính là bài học từ IBM Watson (input metric không cứu được dự án).

3. Metric hoặc giả định đã sửa sau red-team là:
   **V1:** "Đo D14 compliance bằng self-report survey duy nhất."
   **V2:** "Triangulate compliance bằng (self-report) × (photo log ≥ 3/tuần) × (swap rate trong healthy band). Chỉ count compliance khi có ≥ 1 signal khách quan."
   **Vì sao sửa này tốt hơn:** Self-report bị social desirability bias — mẹ bầu ngại nói "không làm theo bác sĩ". Triangulation tránh lặp lại lỗi Watson (đo activity không đo outcome). Cũng học từ Morgan Stanley — họ ghép active usage với citation accuracy + time-saved chứ không tin một metric duy nhất.

   **V1 (bổ sung):** "Owner workflow ghi là 'product team'."
   **V2:** "Mỗi metric có owner role cụ thể (Product Lead, AI Eng Lead, Clinical Lead, Finance BP). Clinical Lead là dietitian partner độc lập, không phải nhân viên nội bộ → tránh conflict of interest khi audit."

4. Trước khi scale, cần phải:
   1. Đạt **menu safety audit pass rate ≥ 98%** trong 3 tháng liên tiếp với cohort GDM và IDA, kèm 0 sự cố y tế nghiêm trọng.
   2. Ký MOU với **≥ 5 phòng khám sản** để có kênh distribution đáng tin cậy + nguồn ground truth HbA1c thật (chuyển clinical outcome proxy từ self-report sang lab data).
   3. Build **food recognition model accuracy top-1 ≥ 75%** trên 100 món Việt phổ biến + correction rate ≤ 25% (gate cho photo logging workflow).
```

---

## 6. Red-team và sửa v2

| Red-team risk | Metric / giả định bị chất vấn | Sửa gì ở v2? |
|---|---|---|
| 1. **CFO**: "Compliance ≥ 50% không trả lời được câu — app có giúp giảm chi phí khám thai bất thường, NICU admission, hay không? ROI ở đâu?" | Compliance D14 + retention D30 không có liên kết đến cost/value thực tế | Thêm metric **Clinical outcome proxy** (% GDM user đường huyết trong target zone) ở layer Value của Workflow 2. Lộ trình: V1 self-report → V2 lấy HbA1c thật qua MOU phòng khám. |
| 2. **User**: "Tactic push notification W2 có ép mẹ bầu cảm thấy có lỗi khi không ăn theo menu — gây thêm anxiety thay vì giảm anxiety không?" | Tactic 3 (push notification W2) có thể tạo guilt/anxiety, ngược với mục tiêu sản phẩm | V2: đổi tone notification từ "bạn mới đạt 60%" sang "tuần này thai 27 tuần, cùng xem món nào dễ thêm sắt nhé"; thêm metric **anxiety self-report (PHQ-2)** weekly trong 4 tuần đầu, target *không tăng* so với baseline. |
| 3. **Workflow Owner**: "Dietitian audit 5% menu/tuần là 1 người làm — không scale được khi user > 500; ai backup khi dietitian nghỉ phép?" | Audit pipeline phụ thuộc 1 người (single point of failure) | V2: ký với 2 dietitian partner (1 chính + 1 backup); standardize audit checklist thành Google Form để bất kỳ dietitian có chứng chỉ đều có thể audit; tự động sample random thay vì dietitian chọn. |

### Ít nhất 2 thay đổi cụ thể từ v1 sang v2

| # | V1 có vấn đề gì? | V2 sửa thành gì? | Vì sao sửa này tốt hơn? |
|---|---|---|---|
| 1 | D14 menu compliance đo bằng self-report duy nhất | Triangulate self-report × photo log ≥ 3/tuần × swap rate healthy band; chỉ count khi có ≥ 1 signal khách quan | Tránh social desirability bias; học từ Watson — không dừng ở metric "AI đã làm gì" mà phải có signal khách quan |
| 2 | Value layer chỉ có CAC/cost — không có outcome lâm sàng | Thêm clinical outcome proxy (% user đường huyết trong target zone sau 4 tuần); lộ trình HbA1c thật qua partnership phòng khám | Trả lời được câu CFO "ROI ở đâu" và câu Risk "có giúp y tế thật không" — chứ không chỉ "app dễ dùng" |
| 3 | Tactic push notification W2 có nguy cơ tăng anxiety; không có metric đo tác dụng phụ | Đổi tone supportive thay vì pressure; thêm anxiety self-report (PHQ-2) weekly với target *không tăng* | Sản phẩm dành cho mẹ bầu — nếu giảm anxiety là core value, phải đo và bảo vệ chính metric đó, không để adoption tactic phá hỏng |

---

## 7. Checklist trước khi nộp

- [x] Có 1 product cụ thể, không chọn "AI cho cả công ty". → **NestAI** cho mẹ bầu GDM/IDA tại VN.
- [x] Có 2-4 workflow chính. → **4 workflow**: Onboarding, Menu Generation, Photo Logging, Safety Escalation.
- [x] Mỗi workflow có vai trò AI, human review và failure path.
- [x] Có rào cản ADKAR chính. → **Knowledge + Ability**, phụ là Reinforcement.
- [x] Dashboard có metric toàn product và metric theo workflow.
- [x] Không chỉ đo usage: login, prompt count, DAU/MAU. → Có compliance, audit pass rate, clinical outcome proxy, correction rate.
- [x] Có baseline, target, data source và owner cho các metric chính.
- [x] Có ít nhất 1 metric Quality, Trust hoặc Value. → Menu safety audit pass rate, swap rate, clinical outcome proxy, incident rate.
- [x] Có Red-team risk và Fix.
- [x] Có ít nhất 2 thay đổi rõ từ v1 sang v2. → **3 thay đổi** (compliance triangulation, clinical outcome proxy, anxiety guardrail).
- [x] Decision Memo có continue / pivot / kill. → **Continue with guardrails** + 3 gate trước khi scale.
