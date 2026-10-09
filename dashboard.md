# OPERATING DASHBOARD — CareerX (EDU-17)

**Loại mô hình:** B2C · **Cập nhật:** 09/10/2026 · Vũ Quốc Bảo – 2A202602829
**NORTH STAR:** Activation rate (tải CV đã tối ưu theo JD trong 24h đầu) — hiện tại: chưa đo (0 user) — mục tiêu: đặt sau baseline pilot (~02/11/2026). Chuyển sang Retention khi có số (~18/11/2026).

### Đèn báo sớm (Leading — nhìn hằng ngày/tuần)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| #1 Activation rate | chưa đo | ≥ baseline +30% / quanh baseline / < baseline | [TB] | #4 Trial → paid |
| #2 Retention (CV thứ 2, JD khác, ≤30 ngày) | chưa đo | ≥ cohort trước / thấp hơn baseline / giảm 2 cohort liên tiếp | [TB] | #8 LTV/CAC |
| #3 p95 cost/job ÷ giá bán (chi phí AI) | chưa đo (TB mô hình 17,9%) | ≤26,5% / 26,5–33,5% / >33,5% | [MH] | #7 Gross Margin |

### Đèn vận hành (Operating — nhìn hằng tuần/tháng)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn | Báo trước cho |
|---|---|---|---|---|
| #4 Trial → paid | chưa đo | ≥8,5% / 5–8,5% / <5% | [BM] 09/10/2026 | #8 LTV/CAC |
| #5 Chi phí free tier ÷ chi phí biến đổi | chưa đo (ước tính 30% nếu 1 CV + job free rẻ ½) | ≤33% / 33–47% / >47% | [MH] | #7 Gross Margin |
| #6 Containment rate | chưa đo (ước tính 70%) | ≥48,5% / 38,8–48,5% / <38,8% | [MH] | #7 Gross Margin |

### Đèn kết quả (Lagging — nhìn hằng quý)

| Đèn | Hiện | 🟢 / 🟡 / 🔴 | Nguồn |
|---|---|---|---|
| #7 Gross Margin thực (gồm free tier) | chưa đo (mô hình 72,3% chưa tính free tier) | ≥60% / 50–60% / <50% | [MH] |
| #8 LTV/CAC | n/a (Tháng 1 CAC ≈ 0) | ≥3 / 2–3 / <2 | [BM] 09/10/2026 |

### 5 luật quyết định (⏹ = luật dừng)

1. ⏹ **NẾU** free tier ÷ chi phí biến đổi (#5) >47% **TRONG** 2 tháng liên tiếp **VÀ** ≥100 job free/tháng **THÌ** dừng cấp CV miễn phí cho user đăng ký mới sprint kế tiếp **KHÔNG THÌ** không tăng quota miễn phí để kéo user.
2. ⏹ **NẾU** containment (#6) <38,8% **TRÊN** 100 job gần nhất **THÌ** dừng mời user mới, sửa prompt/rubric tới khi ≥48,5% trên 50 job tiếp **KHÔNG THÌ** không mở ngách hay kênh mới để "bù" job hỏng.
3. ⏹ **NẾU** activation (#1) < baseline **TRONG** 2 cohort tuần liên tiếp **VÀ** mỗi cohort ≥8 đăng ký (chênh ≤1 người = bằng nhau) **THÌ** đóng băng mời user 1 tuần, phỏng vấn 5 SV bỏ dở, sửa bước rớt nhiều nhất **KHÔNG THÌ** không làm thêm tính năng (extension, STAR).
4. **NẾU** trial → paid (#4) <5% **TRONG** 2 cohort tháng liên tiếp **VÀ** mỗi cohort ≥100 đăng ký **THÌ** phỏng vấn 10 user hết CV free không mua, đổi đúng một thứ: gói bán hoặc thông điệp hết quota **KHÔNG THÌ** không giảm giá dưới giá sàn $0,823/job.
5. **NẾU** retention (#2) giảm so với cohort trước **TRONG** 2 cohort liên tiếp **VÀ** mỗi cohort ≥30 user có CV đầu **THÌ** thu hẹp vào 1 ngách (SV năm cuối 1 trường), thử gói 7 ngày **KHÔNG THÌ** không tăng chi acquisition.

### Cổng gác 90 ngày (ngày 0 = 19/10/2026)

| Ngày | Metric (1) | Ngưỡng qua cổng | Bằng chứng | Nếu trượt |
|---|---|---|---|---|
| 30 (18/11/2026) — cổng học | Activation rate baseline | Có số trên ≥15 user đăng ký; aha moment đã định nghĩa; báo số tuyệt đối | Bảng cohort từ log sự kiện | FIX (sửa tracking) |
| 60 (18/12/2026) | Retention 30 ngày | ≥2 khối cohort 2 tuần đủ 30 ngày, mỗi khối ≥8 user có CV đầu, khối sau ≥ khối trước (chênh ≤1 người = bằng nhau). Thiếu mẫu = "chưa đủ mẫu" → FIX, không phải GO | Bảng retention theo cohort, số tuyệt đối | FIX (thu hẹp ngách / gói 7 ngày), lần 2 PIVOT |
| 90 (17/01/2027) | Trial → paid | ≥5% trên ≥100 đăng ký; thanh toán phải bật trước 02/12/2026 (hạn tuyệt đối 18/12/2026) | Báo cáo cohort tháng + sổ giao dịch | FIX một lần (30 ngày), sau đó PIVOT hoặc KILL |

Ở cổng ngày 60, "cohort" nghĩa là khối 2 tuần (các chỗ khác trong bài cohort = tuần). Cổng ngày 90 giả định ≥100 đăng ký, dựa vào kế hoạch 300 đăng ký ở Tháng 2–3 từ landing page.

**KILL CRITERIA:** KILL bán lẻ cho cá nhân vào 18/03/2027 (ngày 150) nếu, sau đúng 1 lần FIX (17/01–16/02/2027), cohort đăng ký trong thời gian FIX (đủ 30 ngày vào 18/03) có trial → paid <5% trên ≥100 đăng ký, hoặc GM thực <50% trên ≥30 job paid trong tháng FIX. Nếu luật 4 đã dùng lần FIX trước ngày 90 thì tính lại mốc theo cùng cách. Rủi ro: Tết Âm lịch (~06/02/2027) nằm trong tháng FIX; được lùi mốc **một lần, tối đa 2 tuần (tới 01/04/2027)**, chỉ khi số đăng ký trong tuần Tết thấp hơn một nửa trung bình hai tuần liền trước đó.

**CHƯA ĐO ĐƯỢC:**
- **Mọi đèn** (0 user, chưa log): cần event tracking + log token theo job, tách free/paid, cờ `is_internal`. Activation ~02/11/2026, Retention từ ~18/11/2026 (baseline ~02/12/2026), p95 cost và containment từ pilot (bắt đầu 19/10/2026; eval 30 CV × 3 JD hạn 15/10/2026).
- **Trial → paid, GM thực, LTV/CAC (#4, #7, #8):** cần thanh toán + paywall (Tháng 2–3, hạn 02/12/2026). Tháng 1 mời trực tiếp nên CAC ≈ 0 và #8 chưa tính được. Mục tiêu CAC = LTV 90 ngày ÷ 3 ≈ $1,6 (từ $4,8 ÷ 3), cập nhật khi có LTV thật; ngân sách CAC $69,4 trong mô hình giả định khách ở lại 12 tháng nên chỉ là trần lý thuyết.
- **Mức giảm ½ chi phí job miễn phí** (model rẻ hơn / ít lượt hơn) chưa kiểm chứng; nếu không đạt thì #5 ≈ 46,7%, GM thực tháng đầu ≈ 50%.
- **p95/trung bình** chưa biết nên ngưỡng #3 có thể chặt hơn mức cần. Pilot 15–30 SV nên mọi số báo kèm số tuyệt đối.

<div style="page-break-before: always"></div>

# PHỤ LỤC [MH] — phép tính (trang 2)

Số đầu vào từ `VuQuocBao_Day22_model.xlsx` (đính kèm trong repo): v = chi phí biến đổi/job đã bắt đầu = 0,177128 $ (`1_Cost_Job` B31+B38+B43+B47) · q = QA/job = 0,015 $ (`2_Pricing!B30`) · P = 0,99 $ (`2_Pricing!B19`) · ARPU = 8 $/tháng (`4_Channel_Fit!B5`) · containment ước tính R = 70% (chưa đo). Quy ước GM: 🟢 ≥60%, 🔴 <50% (`2_Pricing!B23`).

**[MH] 1 — #6 Containment:** R ≥ (v + q) ÷ (P × (1 − GM)). GM 60%: 0,192128 ÷ 0,396 = **48,5%**. GM 50%: 0,192128 ÷ 0,495 = **38,8%**.

**[MH] 2 — #3 p95 cost/job ÷ giá:** v ≤ P × (1 − GM) × R − q. GM 60%: 0,396 × 0,7 − 0,015 = 0,2622 $ → **26,5%** giá. GM 50%: 0,495 × 0,7 − 0,015 = 0,3315 $ → **33,5%**. (Trần suy từ chi phí trung bình, đèn đo p95: chặt hơn mức cần; chỉ đúng khi R = 70%.)

**[MH] 3 — #5 Free tier:** 1 khách trả tiền = 8 job hoàn tất ÷ 0,7 = 11,43 job đã bắt đầu → chi phí biến đổi 2,024 $, QA 0,171 $, COGS trả tiền 2,196 $. Ngân sách free tối đa F = 8 × (1 − GM) − 2,196: GM 60% → 1,004 $ → F ÷ (F + 2,024) = **33,2%**; GM 50% → 1,804 $ → **47,1%**.
Đối chiếu (chuyển đổi 10% → 10 lượt đăng ký, tức 10 job free với 1 CV/user; ước tính thô): 1 CV cùng chi phí 1,77 $ → 46,7% (GM thực ≈ 50,4%); 1 CV, chi phí job free ½ → 0,89 $ → **30,4%** (GM thực ≈ 61,5%); 3 CV → 72% (GM thực ≈ 6%).

**[BM]:** trial → paid app AI 8,5% vs non-AI 5,6% (RevenueCat *State of Subscription Apps 2026*, qua TechCrunch 10/03/2026; kiểm tra 09/10/2026). LTV/CAC ≥3: Bessemer *Scaling to $100 Million* (21/09/2021), David Skok *SaaS Metrics 2.0* (kiểm tra 09/10/2026; cả hai nguồn nói về SaaS B2B).
