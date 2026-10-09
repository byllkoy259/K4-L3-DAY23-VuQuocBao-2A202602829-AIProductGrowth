# Worksheet — CareerX (EDU-17, Trợ lý nghề nghiệp X)

Họ tên: Vũ Quốc Bảo · MSSV: 2A202602829 · Ngày làm: 09/10/2026

## Trạm 1 — Loại mô hình

**Câu chốt loại:** Chúng tôi là B2C vì tiền đến từ chính sinh viên, người dùng thật cũng là sinh viên đó, và chúng tôi chạm trực tiếp họ qua web app CareerX (sau này thêm Chrome extension), nơi giữ CV và lịch sử sử dụng của họ. Phía nhà tuyển dụng và partner trường chỉ là giả thuyết Tháng 4+, chưa có nên không đưa vào bảng đèn.

**Hiện trạng (09/10/2026):** 0 user thật, chưa log sự kiện/token, chưa có paywall. Job = "1 CV được tối ưu theo 1 JD và sinh viên tải bản đã sửa". Aha moment = đúng sự kiện này (tải bản CV đã tối ưu theo JD). Mock interview STAR là tính năng/job thứ 2 (Tháng 4+).

**Bảng đèn B2C của đề bài (HANDBOOK §3.1):**

| Đèn | ✅ / 🔧 / ❌ | Số nằm ở đâu / cần gì để đo |
|---|---|---|
| Đường cong retention (D1/D7/D30/D60) | ❌ | Cần user thật + log sự kiện. Pilot bắt đầu 19/10/2026 → D7 có cuối 10/2026, D30 giữa 11/2026 |
| Activation rate | 🔧 | Cần event tracking sự kiện "tải CV đã tối ưu" trong 24h đầu kể từ đăng ký |
| p95 cost/user/tháng ÷ ARPU | 🔧 | Có Cost/Job mô hình $0,274 (2_Pricing!B5); thiếu log token theo user |
| Trial → paid | ❌ | Chưa có paywall; landing + thanh toán dự kiến Tháng 2–3 |
| Retention M12 | ❌ | Sản phẩm chưa chạy đủ 12 tháng |
| Chi phí free tier ÷ tổng COGS | 🔧 | Mô hình chưa tính free tier (One-Pager Day 22 ghi 3 CV miễn phí; kế hoạch hiện tại sau [MH] 3 là 1 CV); cần log token tách job free / job trả tiền |
| Tỷ lệ refund | ❌ | Chưa có giao dịch |
| LTV/CAC · CAC payback · GM | GM 🔧 · LTV/CAC ❌ | GM 72,3% là số mô hình (2_Pricing!B21), chưa đo; ngân sách CAC $69,4 / payback 12 tháng có (4_Channel_Fit!B9), chưa có ô LTV |

## Trạm 2 — Thẻ đèn

**North Star:** Activation rate (tải bản CV đã tối ưu theo JD trong 24h đầu) — hiện tại: chưa đo (0 user) — mục tiêu: chưa đặt, lấy baseline từ pilot bắt đầu 19/10/2026 rồi đặt ở Trạm 3. Khi đủ dữ liệu (từ ~18/11/2026) North Star chuyển sang Retention.

**Lưu ý trung thực:** hiện chưa có user thật, chưa có log, mọi đèn dưới đây chưa có số đo. Pilot chỉ 15–30 sinh viên nên mọi số phải báo kèm số tuyệt đối (ví dụ "6/20 người"), không chỉ %.

**Quy ước chung cho mọi đèn:**
- **Tài khoản test** = email trong danh sách nhóm dev, gắn cờ `is_internal` trong log. Luôn loại khỏi mọi đèn.
- **Giờ và tuần:** mọi mốc 24h, 30 ngày, tuần cohort tính theo giờ Việt Nam (UTC+7); tuần chạy từ thứ Hai đến Chủ nhật.
- **"Cohort" = tuần** (thứ Hai–Chủ nhật), trừ cổng ngày 60 ở Trạm 5, nơi cohort = khối 2 tuần để đủ mẫu pilot (hai khối đầu đăng ký đến 15/11/2026 đủ 30 ngày vào 15/12/2026).
- **Cohort chưa đủ cửa sổ** (ví dụ chưa đủ 30 ngày) ghi "đang chờ", không tính vào tỷ lệ.
- **Job đã bắt đầu** = sinh viên đã nộp cả CV và JD. **Job hoàn tất** = sinh viên đã tải bản CV đã sửa.
- **Job free / paid** xét theo từng job: free khi dùng quota miễn phí hoặc lượt thưởng, paid khi dùng lượt đã mua (không xét theo trạng thái user).

| # | Tầng (L/O/G) | Đèn | Định nghĩa (đếm gì · **không** đếm gì) | Công thức | Nhịp · ai lấy số | Báo trước cho |
|---|---|---|---|---|---|---|
| 1 | L | Activation rate | **Đếm:** user mới đăng ký có ≥1 job hoàn tất (tải bản CV đã sửa) trong 24h kể từ lúc đăng ký. **Không đếm:** CV bỏ dở hoặc chỉ xem trước không tải, tải sau 24h. | user mới có job hoàn tất trong 24h ÷ user mới đăng ký cùng cohort tuần | Nhìn hằng ngày, chốt theo tuần · Quốc Bảo từ log sự kiện | #4 Trial → paid |
| 2 | L | Retention (user quay lại) | **Đếm:** user đã có job hoàn tất đầu tiên, rồi tạo thêm ≥1 job hoàn tất cho một **JD khác** trong 30 ngày sau job đầu. Hai JD là một nếu cùng link tin tuyển dụng hoặc cùng nội dung sau khi bỏ khoảng trắng. **Không đếm:** sửa lại CV cho cùng một JD, user chưa từng có job hoàn tất (không nằm trong mẫu số). | user có job hoàn tất thứ 2 (JD khác) trong 30 ngày ÷ user có job hoàn tất đầu tiên trong cohort (chỉ cohort đã đủ 30 ngày) | Hằng tuần theo cohort · Quốc Bảo; số đầu tiên ~18/11/2026 | #8 LTV/CAC |
| 3 | L | p95 cost/job ÷ giá bán (đèn chi phí AI) | **Đếm:** chi phí biến đổi thật (LLM + infra + retry, từ log token) của **từng job đã bắt đầu**, gồm cả job bỏ dở/lỗi vì vẫn tốn token, cả job free và paid; lấy phân vị 95 trong kỳ, chia cho giá bán $0,99. **Không đếm:** QA/HITL, overhead/R&D. Cần ≥20 job trong kỳ, ít hơn ghi "chưa đủ mẫu". Dùng cost/job thay cost/user vì pilot chưa đủ user. | p95(chi phí biến đổi mỗi job đã bắt đầu) ÷ $0,99 | Hằng tuần · Hoàng lấy từ log token | #7 Gross Margin |
| 4 | O | Trial → paid | **Đếm:** user đăng ký có giao dịch trả tiền thành công đầu tiên trong 30 ngày kể từ ngày đăng ký. **Không đếm:** giao dịch bị hoàn tiền; cohort chưa đủ 30 ngày. | user có giao dịch đầu tiên ≤30 ngày ÷ user đăng ký cùng cohort | Hằng tháng · Quốc Bảo; có số từ Tháng 2–3 (khi có thanh toán) | #8 LTV/CAC (qua số khách trả tiền mới ở mẫu số của CAC) |
| 5 | O | Chi phí free tier ÷ tổng chi phí biến đổi | **Đếm:** chi phí biến đổi (LLM + infra + retry) của các job free (quota CV miễn phí, kế hoạch hiện tại là 1 CV/user, kể cả CV miễn phí của user sau này trả tiền, + lượt thưởng giới thiệu), chia cho tổng chi phí biến đổi của mọi job. **Không đếm:** QA, overhead. | chi phí biến đổi job free ÷ chi phí biến đổi mọi job | Hằng tháng · Hoàng log tách job free/paid | #7 Gross Margin |
| 6 | O | Containment rate | **Đếm:** job hoàn tất ÷ job đã bắt đầu. Job bỏ dở hoặc AI báo không xử lý được = không hoàn tất (và không tính tiền). | job hoàn tất ÷ job đã bắt đầu | Hằng tuần · Hoàng từ log; eval 30 CV × 3 JD hạn 15/10/2026 | #7 Gross Margin (breakeven containment 48,5% trong mô hình) |
| 7 | G | Gross Margin (GM thực, gồm free tier) | **Đếm:** (doanh thu − COGS) ÷ doanh thu trong tháng. Doanh thu ghi nhận khi job hoàn tất (không tính tiền nạp chưa dùng), trừ hoàn tiền. COGS = chi phí biến đổi LLM/infra/retry của mọi job (cả free) + QA + phí cổng thanh toán. **Không đếm:** R&D, lương đội, overhead. Tháng doanh thu = 0 ghi "n/a" (pilot chưa có paywall nên chưa có số). Nhãn rõ: **GM mô hình 72,3% (chưa free tier)** ≠ **GM thực (gồm free tier)**. | (doanh thu − COGS gồm cả free tier) ÷ doanh thu | Hằng quý, xem tháng · Quốc Bảo | — (đèn kết quả, bảng điểm) |
| 8 | G | LTV/CAC | **Đếm:** LTV = doanh thu thực thu 90 ngày đầu trên mỗi khách trả tiền × GM thực (#7). CAC = chi phí marketing trực tiếp + thưởng giới thiệu ÷ khách trả tiền mới cùng kỳ. **Không đếm:** lương đội, giao dịch bị hoàn tiền. Tháng 1 mời trực tiếp nên CAC ≈ 0: ghi "n/a khi CAC = 0", có số từ Tháng 2–3. | LTV ÷ CAC | Hằng quý · Quốc Bảo | — (đèn kết quả, bảng điểm) |

Đèn chi phí AI là đèn số: **#3 (p95 cost/job ÷ giá bán)**, hỗ trợ bởi #5 (chi phí free tier). Tổng: 8 đèn (3 L · 3 O · 2 G).

**Ước tính thô về rủi ro free tier (chưa phải số đo):** nếu 10% user chuyển trả tiền và ai cũng dùng hết quota miễn phí thì mỗi người trả tiền kéo theo 10 lượt đăng ký, tức 10 × (số CV miễn phí mỗi user) job free. Với 3 CV: 30 job free ≈ $5,3, gần bằng ARPU $8/tháng, GM thực tháng đầu chỉ ~6%. Chi tiết và phương án 1 CV ở phụ lục [MH] 3. GM thực có thể thấp hơn nhiều so với 72,3%.

## Trạm 3 — Ngưỡng

Quy ước GM: **🟢 ≥60% · 🟡 50–60% · 🔴 <50%**, lấy từ đèn Gross Margin của file model (`2_Pricing!B23`). Đây là quy ước của bài tập, không phải benchmark ngành.

| # | Đèn | 🟢 | 🟡 | 🔴 | Nguồn | Lý do (1 câu) · ngày kiểm tra nếu [BM] |
|---|---|---|---|---|---|---|
| 1 | Activation rate | ≥ baseline +30% | quanh baseline | < baseline | [TB] | Chưa có chuẩn, đo 2 cohort tuần của pilot (19–25/10 và 26/10–01/11/2026) rồi lấy baseline, dự kiến có số ~02/11/2026; mẫu rất nhỏ (15–30 SV) nên báo kèm số tuyệt đối. |
| 2 | Retention (quay lại ≤30 ngày) | cohort sau ≥ cohort trước và ổn định qua 2 cohort | thấp hơn baseline nhưng chưa giảm 2 cohort liên tiếp | giảm 2 cohort liên tiếp | [TB] | Chưa có chuẩn cho sản phẩm dùng theo mùa nộp hồ sơ; cohort đầu đủ 30 ngày ~18/11/2026, baseline 2 cohort dự kiến ~02/12/2026. |
| 3 | p95 cost/job ÷ giá bán | ≤26,5% | 26,5–33,5% | >33,5% | [MH] | Trần suy từ GM 60%/50% ở containment 70% (phụ lục [MH] 2); hiện chỉ có mức trung bình mô hình 17,9%, p95 chưa đo, chờ pilot. |
| 4 | Trial → paid | ≥8,5% | 5–8,5% | <5% | [BM] | Trung vị trial→paid: app AI 8,5%, non-AI 5,6% (RevenueCat, *State of Subscription Apps 2026*, công bố 19/03/2026, qua TechCrunch 10/03/2026). **Ngày kiểm tra: 09/10/2026.** Lưu ý độ so sánh: số này đo từ lượt dùng thử sang trả tiền, còn #4 đo từ đăng ký (gói miễn phí) sang trả tiền trong 30 ngày, nên số thật của CareerX nhiều khả năng thấp hơn. KPI kế hoạch ≥10% cao hơn trung vị 8,5% và cao hơn Duolingo 9,0% (Q2/2026, 05/08/2026): cần ghi lý do hoặc hạ mục tiêu. |
| 5 | Chi phí free tier ÷ chi phí biến đổi | ≤33% | 33–47% | >47% | [MH] | Phần free tối đa còn lại sau khi chi phí khách trả tiền đã chiếm $2,20/tháng, để GM thực ≥60% / ≥50% (phụ lục [MH] 3). |
| 6 | Containment rate | ≥48,5% | 38,8–48,5% | <38,8% | [MH] | Containment tối thiểu để GM đạt 60% / 50% ở giá $0,99 (phụ lục [MH] 1). |
| 7 | Gross Margin (thực, gồm free tier) | ≥60% | 50–60% | <50% | [MH] | Theo quy ước GM của file model; GM 72,3% hiện tại chưa tính free tier nên không dùng để chấm đèn này. |
| 8 | LTV/CAC | ≥3 | 2–3 | <2 | [BM] | Bessemer, *Scaling to $100 Million* (21/09/2021): "invest in customer acquisition when CLTV/CAC are 3x+"; David Skok, *SaaS Metrics 2.0*: "best SaaS businesses have a LTV to CAC ratio higher than 3". **Ngày kiểm tra: 09/10/2026.** Cả hai nguồn nói về SaaS B2B, không phải B2C AI, và nguồn Bessemer đã cũ (2021), chưa có bản mới thay thế. Mốc đỏ <2 là cách chia của tôi, khớp luật B2C-5 trong tài liệu đề bài (HANDBOOK §3.1, đã gỡ khỏi repo này). Chưa có CAC thật (Tháng 1 mời trực tiếp), có số từ Tháng 2–3. |

### Phụ lục [MH] — phép tính (≥2)

**[MH] 1 — #6 Containment rate**

```
Đầu vào (từ file model): v = chi phí biến đổi/job đã bắt đầu = 0,1316 (LLM) + 0 (speech) + 0,035 (infra) + 0,010528 (retry) = 0,177128 $ (1_Cost_Job B31+B38+B43+B47)
                        q = QA/job đã bắt đầu = 0,05 × (2/60) × 9 = 0,015 $ (2_Pricing!B30)
                        P = giá bán = 0,99 $ (2_Pricing!B19) · biến thể HITL A nên chi phí escalate e = 0
Phép tính: R ≥ (v + q) ÷ (P × (1 − GM))
  GM 60%: 0,192128 ÷ (0,99 × 0,40) = 0,192128 ÷ 0,396 = 0,4852
  GM 50%: 0,192128 ÷ (0,99 × 0,50) = 0,192128 ÷ 0,495 = 0,3881
Kết quả → 🟢 ≥48,5% · 🟡 38,8–48,5% · 🔴 <38,8%  (containment hiện tại 70% là ước tính, chưa đo)
```

**[MH] 2 — #3 p95 cost/job ÷ giá bán**

```
Đầu vào: v (chi phí biến đổi/job đã bắt đầu) hiện = 0,177128 $ · q = 0,015 $ · P = 0,99 $ · R = 70% (ước tính, phụ thuộc đèn #6)
Phép tính: cost/job hoàn tất = (v + q) ÷ R ≤ P × (1 − GM)  ⇒  v ≤ P × (1 − GM) × R − q
  GM 60%: v ≤ 0,396 × 0,7 − 0,015 = 0,2622 $  ⇒ 0,2622 ÷ 0,99 = 26,5%
  GM 50%: v ≤ 0,495 × 0,7 − 0,015 = 0,3315 $  ⇒ 0,3315 ÷ 0,99 = 33,5%
Kết quả → 🟢 ≤26,5% · 🟡 26,5–33,5% · 🔴 >33,5%  (hiện 0,177128 ÷ 0,99 = 17,9%, mức TRUNG BÌNH)
Lưu ý: trần suy từ chi phí trung bình, còn đèn đo p95. p95 luôn ≥ trung bình nên áp trần này cho p95 là chặt hơn mức cần; hệ số p95/trung bình chưa biết, chờ pilot. Ngưỡng chỉ đúng khi containment = 70%.
```

**[MH] 3 — #5 Chi phí free tier ÷ chi phí biến đổi**

```
Đầu vào: ARPU = 8 $/tháng (4_Channel_Fit!B5) · 8 job hoàn tất/khách/tháng · R = 70% · v = 0,177128 · q = 0,015
Phép tính:
  Job đã bắt đầu của 1 khách trả tiền = 8 ÷ 0,7 = 11,43/tháng
  Chi phí biến đổi khách trả tiền = 11,43 × 0,177128 = 2,024 $ · QA = 11,43 × 0,015 = 0,171 $ · COGS trả tiền = 2,196 $
  Ngân sách free tối đa F = 8 × (1 − GM) − 2,196
    GM 60%: F = 3,2 − 2,196 = 1,004 $  ⇒ tỷ lệ = F ÷ (F + 2,024) = 1,004 ÷ 3,028 = 33,2%
    GM 50%: F = 4,0 − 2,196 = 1,804 $  ⇒ tỷ lệ = 1,804 ÷ 3,828 = 47,1%
Kết quả → 🟢 ≤33% · 🟡 33–47% · 🔴 >47%
Đối chiếu kế hoạch (ước tính thô, chưa đo; giả định mọi user đăng ký dùng hết quota, chuyển đổi 10%, ARPU 8 $ một tháng).
Theo quy ước job free/paid xét theo từng job, CV miễn phí của chính người trả tiền cũng là job free, nên mỗi khách trả tiền ứng với 10 lượt đăng ký:
  3 CV free: 10 × 3 = 30 job free = 5,31 $ ⇒ tỷ lệ 72% (🔴) · GM thực tháng đầu của cohort ≈ 6%
  1 CV free, cùng chi phí/job: 10 job free = 1,77 $ ⇒ tỷ lệ 46,7% (sát ranh giới 🟡/🔴) · GM thực ≈ 50,4%
  1 CV free, chi phí job free giảm một nửa: 0,89 $ ⇒ tỷ lệ 30,4% (🟢) · GM thực ≈ 61,5%
```

**Quyết định kế hoạch từ [MH] 3 (09/10/2026):** giảm gói miễn phí từ 3 CV xuống **1 CV**, và giảm chi phí mỗi job miễn phí xuống khoảng một nửa (model rẻ hơn và/hoặc ít lượt hơn). **Mức giảm một nửa là điều kiện sống còn của quyết định này**: nếu chỉ giảm số CV mà chi phí/job giữ nguyên thì đèn #5 ≈ 46,7% (sát đỏ) và GM thực tháng đầu ≈ 50%. Mức giảm phải được đo bằng log token của pilot. One-Pager Day 22 vẫn ghi 3 CV miễn phí, cần sửa cho thống nhất nếu nộp cùng.

## Trạm 4 — 5 luật quyết định

⏹ = luật dừng. Ngưỡng lấy từ bảng Trạm 3. Pilot chỉ có 15–30 sinh viên nên các luật có vế VÀ (mẫu tối thiểu) để không phản ứng với nhiễu; luật 1, 4 và 5 chưa thể kích hoạt trong pilot, chỉ kích hoạt được khi có ~300 đăng ký (Tháng 2–3): luật 1 cần ≥100 job free mỗi tháng, tức ≥100 đăng ký (mỗi user 1 CV free), luật 4 cần ≥100 đăng ký mỗi cohort, luật 5 cần ≥30 user mỗi cohort.

1. ⏹ **NẾU** chi phí free tier ÷ chi phí biến đổi (#5) >47% **TRONG** 2 tháng liên tiếp **VÀ** có ≥100 job free trong mỗi tháng **THÌ** dừng cấp CV miễn phí cho user đăng ký mới trong sprint kế tiếp, chỉ giữ cho user đã đăng ký, và chuyển job miễn phí sang model rẻ hơn **KHÔNG THÌ** không tăng quota miễn phí để kéo thêm user.
2. ⏹ **NẾU** containment (#6) <38,8% **TRÊN** 100 job đã bắt đầu gần nhất **THÌ** dừng mời user mới và dừng pilot ở số user hiện có, cả đội sửa prompt và rubric trên các CV bị lỗi cho tới khi containment ≥48,5% trên 50 job tiếp theo **KHÔNG THÌ** không mở rộng sang ngách mới hoặc chạy thêm kênh để "bù" số job hỏng.
3. ⏹ **NẾU** activation (#1) thấp hơn baseline **TRONG** 2 cohort tuần liên tiếp **VÀ** mỗi cohort ≥8 user đăng ký (ghi số tuyệt đối, chênh ≤1 người coi là bằng nhau) **THÌ** đóng băng việc mời user mới 1 tuần, phỏng vấn 5 sinh viên đã bỏ giữa chừng và sửa đúng bước rớt nhiều nhất giữa "dán JD" và "tải CV" **KHÔNG THÌ** không làm thêm tính năng mới (Chrome extension, mock interview STAR) để tăng hứng thú.
4. **NẾU** trial → paid (#4) <5% **TRONG** 2 cohort tháng liên tiếp **VÀ** mỗi cohort ≥100 user đăng ký **THÌ** phỏng vấn 10 user đã dùng hết CV miễn phí mà không mua, rồi đổi đúng một thứ cho cohort sau: gói bán (lẻ ↔ gói 7 ngày) hoặc thông điệp ở màn hết quota (không đổi điểm thu tiền, vì job vẫn chỉ tính khi tải) **KHÔNG THÌ** không giảm giá xuống dưới giá sàn $0,823/job (3 × Cost/Job, `2_Pricing!B7`).
5. **NẾU** retention (#2) giảm so với cohort liền trước **TRONG** 2 cohort liên tiếp (tức đèn 🔴 ở Trạm 3) **VÀ** mỗi cohort ≥30 user đã có CV đầu tiên **THÌ** thu hẹp vào đúng một ngách mùa nộp hồ sơ (sinh viên năm cuối của 1 trường/khoa) và thử gói theo mùa (7 ngày, giống Teal+) thay cho bán lẻ từng CV **KHÔNG THÌ** không tăng chi tiêu acquisition để bù cohort quay lại ít.
