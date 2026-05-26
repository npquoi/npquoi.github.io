---
output:
  word_document: default
  html_document: default
---
# BÀI 8: CHỌN MÔ HÌNH VÀ KIỂM ĐỊNH CHỌN MÔ HÌNH

## MỤC TIÊU HỌC TẬP

- Hiểu được tầm quan trọng của việc chọn mô hình trong nghiên cứu kinh tế lượng và hậu quả của việc chọn sai mô hình.
- Nắm vững các thuộc tính của một mô hình hồi quy tốt.
- Phân biệt hai loại sai lầm khi chọn mô hình: bỏ sót biến liên quan (underfitting) và đưa thêm biến không liên quan (overfitting).
- Vận dụng kiểm định RESET của Ramsey để phát hiện hiện tượng bỏ sót biến độc lập.
- Sử dụng các tiêu chuẩn chọn mô hình (Adjusted R², AIC, BIC, F-test, t-test) để so sánh và lựa chọn mô hình phù hợp.
- Áp dụng quy trình thực hành chọn mô hình trong nghiên cứu thực tế.

## TÓM TẮT

Việc chọn mô hình là bước quyết định chất lượng của nghiên cứu kinh tế lượng. Một mô hình tốt phải đồng thời thỏa mãn các tiêu chí: phù hợp với lý thuyết kinh tế, các biến có ý nghĩa thống kê, R² hoặc R² hiệu chỉnh ở mức chấp nhận được, đúng dấu các hệ số, không vi phạm nghiêm trọng các giả thiết cổ điển, có khả năng dự báo tốt và tính tiết kiệm (parsimony) (Gujarati & Porter, 2009, Chương 9).

Hai sai lầm phổ biến khi chọn mô hình là: (1) bỏ sót biến liên quan (underfitting) dẫn đến sai số do thiếu biến (omitted variable bias) khiến ước lượng chệch; và (2) đưa thêm biến không liên quan (overfitting) khiến mô hình kém hiệu quả, phương sai ước lượng tăng và khả năng dự báo giảm (Wooldridge, 2016, Chương 6).

Kiểm định RESET của Ramsey là công cụ phát hiện hiện tượng bỏ sót biến. Các tiêu chuẩn chọn mô hình phổ biến bao gồm: R² hiệu chỉnh, AIC, BIC, kiểm định F (Wald test) và kiểm định J-test. Mỗi tiêu chuẩn có ưu điểm riêng và nên được sử dụng kết hợp (Stock & Watson, 2020, Chương 14).

## THUẬT NGỮ

| Tiếng Anh | Tiếng Việt |
|:---|:---|
| Model Selection | Chọn mô hình |
| Underfitting | Thiếu khớp (bỏ sót biến) |
| Overfitting | Quá khớp (thừa biến) |
| Omitted Variable Bias (OVB) | Sai số do thiếu biến |
| Parsimony | Tính tiết kiệm |
| RESET Test | Kiểm định RESET (Ramsey) |
| Akaike Information Criterion (AIC) | Tiêu chuẩn thông tin Akaike |
| Bayesian Information Criterion (BIC) | Tiêu chuẩn thông tin Bayesian |
| Schwarz Information Criterion (SIC) | Tiêu chuẩn thông tin Schwarz |
| Wald Test | Kiểm định Wald |
| Specification Error | Sai số đặc tả |
| Nested Models | Mô hình lồng nhau |
| Non-nested Models | Mô hình không lồng nhau |

## 8.1. GIỚI THIỆU VỀ VIỆC CHỌN MÔ HÌNH

### 8.1.1. Tại sao chọn mô hình quan trọng?

Trong thực tế nghiên cứu, nhà kinh tế lượng thường đối mặt với câu hỏi: **"Nên đưa bao nhiêu biến vào mô hình? Biến nào nên đưa, biến nào nên bỏ?"** Đây là vấn đề chọn mô hình (model selection) — một trong những bước quan trọng nhất quyết định độ tin cậy của kết quả nghiên cứu (Gujarati & Porter, 2009, Chương 9).

Mô hình quá đơn giản (ít biến) có thể bỏ sót thông tin quan trọng. Mô hình quá phức tạp (nhiều biến) có thể đưa vào nhiều biến không liên quan, làm giảm hiệu quả ước lượng. Theo Wooldridge (2016, Chương 6), chọn mô hình là quá trình **kết hợp giữa lý thuyết kinh tế, bằng chứng thực nghiệm và kỹ năng phán đoán** của nhà nghiên cứu.

### 8.1.2. Vai trò của lý thuyết kinh tế trong chọn mô hình

Lý thuyết kinh tế đóng vai trò **kim chỉ nam** trong việc xác định biến nào nên đưa vào mô hình. Theo Stock và Watson (2020, Chương 14), quy trình nên bắt đầu từ lý thuyết:

**Bước 1:** Dựa trên lý thuyết kinh tế và nghiên cứu trước đó, xác định các biến có thể ảnh hưởng đến biến phụ thuộc. Phân loại: biến bắt buộc (theo lý thuyết), biến kiểm soát (có thể liên quan), biến loại trừ (không liên quan).

**Bước 2:** Ước lượng mô hình đầy đủ nhất, sau đó rút gọn dần dựa trên kiểm định thống kê.

**Ví dụ 8-1:** Theo lý thuyết Keynes, chi tiêu tiêu dùng phụ thuộc chủ yếu vào thu nhập khả dụng. Tuy nhiên, nghiên cứu hiện đại cho thấy lãi suất, lạm phát, kỳ vọng tiêu dùng cũng ảnh hưởng. Do đó, mô hình ban đầu nên bao gồm tất cả biến này, sau đó kiểm định biến nào có ý nghĩa thống kê.

## 8.2. CÁC THUỘC TÍNH CỦA MÔ HÌNH TỐT

Theo Gujarati và Porter (2009, Chương 9), một mô hình hồi quy tốt cần thỏa mãn đồng thời nhiều tiêu chí.

### a) Phù hợp với lý thuyết kinh tế

Hệ số hồi quy phải có **đúng dấu** theo kỳ vọng lý thuyết và có **giá trị hợp lý**.

| Mô hình | Kỳ vọng dấu |
|:---|:---|
| Cầu: Q = f(P, I) | Giá (P) → dấu âm; Thu nhập (I) → dấu dương |
| Sản xuất: Y = f(K, L) | Vốn (K) → dấu dương; Lao động (L) → dấu dương |
| Lương: W = f(Educ, Exp) | Giáo dục → dấu dương; Kinh nghiệm → dấu dương |
| Đầu tư: I = f(r, Y) | Lãi suất (r) → dấu âm; Thu nhập (Y) → dấu dương |

Nếu hệ số có **sai dấu**, đó là tín hiệu cảnh báo mô hình có vấn đề: thiếu biến, đa cộng tuyến, hoặc dữ liệu sai.

### b) Các biến có ý nghĩa thống kê

Các biến đưa vào mô hình phải có ý nghĩa thống kê (thường α = 5% hoặc α = 10%). Tuy nhiên, không nên loại biến chỉ vì p-value > 0,05 — cần cân nhắc lý thuyết kinh tế và vai trò biến kiểm soát (Wooldridge, 2016, Chương 6).

### c) R² hoặc R² hiệu chỉnh ở mức chấp nhận được

**Không có ngưỡng R² "chuẩn"** cho mọi nghiên cứu (Gujarati & Porter, 2009, Chương 9):

- Dữ liệu **chuỗi thời gian** kinh tế vĩ mô: R² từ 0,80–0,95 là phổ biến.
- Dữ liệu **chéo** hành vi cá nhân: R² từ 0,20–0,40 là bình thường.
- Quan trọng hơn R² là: β có ý nghĩa thống kê, đúng dấu, và mô hình không vi phạm giả thiết.

### d) Không vi phạm nghiêm trọng các giả thiết cổ điển

Mô hình phải không có đa cộng tuyến nghiêm trọng (VIF < 10), không có phương sai thay đổi (BP, White), không có tự tương quan (DW, BG), và sai số gần đúng phân phối chuẩn.

### e) Khả năng dự báo tốt và tính tiết kiệm (Parsimony)

Mô hình tốt phải dự báo chính xác cho dữ liệu ngoài mẫu. Nguyên tắc parsimony: **trong số các mô hình có chất lượng tương đương, ưu tiên mô hình đơn giản hơn** (Gujarati & Porter, 2009, Chương 9).

### Bảng 8-1. Các tiêu chí đánh giá mô hình

| Tiêu chí | Câu hỏi | Công cụ đánh giá |
|:---|:---|:---|
| Lý thuyết | Hệ số có đúng dấu? Giá trị hợp lý? | So sánh với lý thuyết kinh tế |
| Ý nghĩa thống kê | Biến có ý nghĩa không? | Kiểm định t (p-value) |
| Giải thích | Mô hình giải thích được bao nhiêu? | R², R² hiệu chỉnh |
| Tổng thể | Mô hình có phù hợp tổng thể? | Kiểm định F |
| Giả thiết cổ điển | Mô hình có vi phạm giả thiết? | Kiểm định BP, White, DW, VIF |
| Dự báo | Dự báo có chính xác? | RMSE, MAE |
| Tiết kiệm | Mô hình có quá phức tạp? | AIC, BIC |

## 8.3. SAI LẦM KHI CHỌN MÔ HÌNH

### 8.3.1. Bỏ sót biến liên quan (Underfitting — Thiếu khớp)

**Bản chất:** Mô hình bỏ sót biến độc lập có liên quan đến biến phụ thuộc, dẫn đến **ước lượng chệch** (Stock & Watson, 2020, Chương 6).

**Cơ chế gây chệch:** Giả sử mô hình đúng gồm X₂ và X₃, nhưng ta chỉ đưa X₂:

$$E(\hat{\alpha}_2) = \beta_2 + \beta_3 \cdot \frac{Cov(X_2, X_3)}{Var(X_2)}$$

Vế thứ hai là **sai số do thiếu biến** (OVB). Sai số này khác 0 khi: (1) X₃ tương quan với X₂, và (2) X₃ ảnh hưởng đến Y.

**Ví dụ 8-2:** Mô hình lương chỉ gồm "Năm học" mà bỏ sót "Kinh nghiệm". Vì kinh nghiệm tương quan với năm học và ảnh hưởng đến lương, hệ số "Năm học" sẽ bị chệch — gánh cả ảnh hưởng của kinh nghiệm.

### 8.3.2. Đưa thêm biến không liên quan (Overfitting — Quá khớp)

**Bản chất:** Mô hình đưa vào biến không thực sự ảnh hưởng đến biến phụ thuộc (Wooldridge, 2016, Chương 6).

**Hậu quả:** Ước lượng vẫn không chệch nhưng kém hiệu quả — phương sai tăng, khoảng tin cậy rộng hơn, bậc tự do giảm, khả năng dự báo có thể giảm.

### Bảng 8-2. So sánh hai loại sai lầm

| Tiêu chí | Underfitting (Thiếu biến) | Overfitting (Thừa biến) |
|:---|:---|:---|
| Ảnh hưởng đến hệ số | **Chệch** và không nhất quán | Không chệch nhưng kém hiệu quả |
| Ảnh hưởng đến SE | Ước lượng sai | Tăng lên |
| Mức độ nghiêm trọng | **Nghiêm trọng hơn** — kết luận sai | Ít nghiêm trọng |
| Cách phát hiện | Kiểm định RESET, lý thuyết | Kiểm định t, AIC, BIC |
| Cách khắc phục | Bổ sung biến | Loại bỏ biến |

**Khuyến nghị:** Khi phân vân, nên **ưu tiên đưa biến vào** hơn là bỏ sót, miễn là có cơ sở lý thuyết. Tuy nhiên, cũng không nên đưa tất cả biến có sẵn.

## 8.4. KIỂM ĐỊNH RESET CỦA RAMSEY

### 8.4.1. Bản chất

Kiểm định RESET (Regression Specification Error Test) được Ramsey (1969) đề xuất, nhằm phát hiện **sai sót đặc tả mô hình**: bỏ sót biến hoặc sai dạng hàm (Gujarati & Porter, 2009, Chương 9).

**Ý tưởng:** Nếu mô hình đúng dạng, các lũy thừa của giá trị dự báo Ŷ (cụ thể Ŷ², Ŷ³) **không nên có ý nghĩa thống kê** khi đưa vào mô hình bổ sung. Nếu chúng có ý nghĩa → mô hình bị sai sót.

### 8.4.2. Quy trình kiểm định

**Giả thuyết:**
- **H₀:** Mô hình không bị sai sót đặc tả.
- **H₁:** Mô hình bị sai sót đặc tả.

**Các bước:**

**Bước 1:** Ước lượng mô hình ban đầu, lấy giá trị dự báo Ŷᵢ.

**Bước 2:** Tính Ŷᵢ², Ŷᵢ³.

**Bước 3:** Ước lượng mô hình bổ sung:

$$Y_i = \beta_1 + \beta_2 X_{2i} + \cdots + \beta_k X_{ki} + \delta_1 \hat{Y}_i^2 + \delta_2 \hat{Y}_i^3 + v_i$$

**Bước 4:** Kiểm định F cho δ₁ = δ₂ = 0:

$$F = \frac{(RSS_{reduced} - RSS_{full}) / q}{RSS_{full} / (n - k - q)} \sim F(q, \, n-k-q)$$

**Bước 5:** Quy tắc quyết định:

| Kết quả | Kết luận |
|:---|:---|
| p-value < α | **Bác bỏ H₀** → Mô hình sai sót → Cần bổ sung biến hoặc đổi dạng hàm |
| p-value ≥ α | **Không bác bỏ H₀** → Không đủ bằng chứng kết luận sai sót |

**Thực hiện trên Stata:**
reg Y X
predict Yhat, xb
gen Yhat2 = Yhat^2
gen Yhat3 = Yhat^3
reg Y X Yhat2 Yhat3
test Yhat2 Yhat3

**Ví dụ 8-3:** Giả sử kết quả: F = 4,25, p-value = 0,023 (α = 5%). Diễn giải: bác bỏ H₀, mô hình sai sót — có thể bỏ sót biến hoặc quan hệ phi tuyến. Cần bổ sung biến kiểm soát hoặc thử hàm logarit.

**Lưu ý:** Kiểm định RESET **không cho biết biến nào bị bỏ sót** — chỉ cho biết mô hình bị sai sót. Nhà nghiên cứu cần dựa vào lý thuyết để xác định biến cần bổ sung.

## 8.5. CÁC TIÊU CHUẨN CHỌN MÔ HÌNH

### 8.5.1. Hệ số xác định hiệu chỉnh (Adjusted R²)

$$\bar{R}^2 = 1 - \frac{RSS/(n-k)}{TSS/(n-1)} = 1 - (1-R^2)\frac{n-1}{n-k}$$

**Quy tắc:** Chọn mô hình có R̄² **cao hơn**. Chỉ so sánh khi cùng biến phụ thuộc. Không phạt đủ nặng biến thừa.

### 8.5.2. Tiêu chuẩn thông tin Akaike (AIC)

$$AIC = n \cdot \ln\left(\frac{RSS}{n}\right) + 2k$$

**Quy tắc:** Chọn mô hình có AIC **nhỏ nhất**. Phạt nặng hơn R̄² khi thêm biến, cân bằng giữa mức phù hợp và tính tiết kiệm.

### 8.5.3. Tiêu chuẩn thông tin Bayesian (BIC)

$$BIC = n \cdot \ln\left(\frac{RSS}{n}\right) + k \cdot \ln(n)$$

**Quy tắc:** Chọn mô hình có BIC **nhỏ nhất**.

**So sánh AIC và BIC:**

| Tiêu chí | AIC | BIC |
|:---|:---|:---|
| Thành phần phạt | 2k | k × ln(n) |
| Mức phạt biến thêm | Nhẹ hơn | **Nặng hơn** (khi n > 7) |
| Xu hướng chọn | Mô hình hơi phức tạp | **Đơn giản hơn** |
| Ưu tiên | Mức phù hợp | Tính tiết kiệm |

**Khuyến nghị:** Nên báo cáo **cả AIC và BIC**. Nếu cả hai cùng chọn một mô hình → kết luận mạnh. Nếu khác nhau → cân nhắc thêm tiêu chí khác.

### 8.5.4. Kiểm định F cho thừa biến (Wald Test) — Mô hình lồng nhau

Khi hai mô hình có quan hệ **lồng nhau** (nested), dùng kiểm định F (Gujarati & Porter, 2009, Chương 8).

**Ví dụ 8-4:**
- Mô hình lớn: Y = β₁ + β₂X₂ + β₃X₃ + β₄X₄ + β₅X₅ + u
- Mô hình nhỏ: Y = β₁ + β₂X₂ + β₃X₃ + u (H₀: β₄ = β₅ = 0)

$$F = \frac{(RSS_{restricted} - RSS_{unrestricted}) / q}{RSS_{unrestricted} / (n - k)} \sim F(q, \, n-k)$$

Trên Stata, lệnh `test X4 X5` tự động thực hiện kiểm định này.

| Kết quả | Kết luận |
|:---|:---|
| p-value < α | **Bác bỏ H₀** → Giữ biến bị loại |
| p-value ≥ α | **Không bác bỏ** → Có thể loại bỏ |

### 8.5.5. So sánh mô hình không lồng nhau (Non-nested Models)

Khi hai mô hình **không lồng nhau**, dùng **kiểm định J-test** (Wooldridge, 2016, Chương 14):

**Bước 1:** Ước lượng Mô hình 2, lấy Ŷ₂. **Bước 2:** Đưa Ŷ₂ vào Mô hình 1: Y = β₁ + β₂X₂ + γŶ₂ + w. **Bước 3:** Kiểm định H₀: γ = 0.

| Kết quả J-test | Kết luận |
|:---|:---|
| Bác bỏ ở cả hai chiều | Cả hai mô hình đều thiếu → Cần mô hình mới |
| Không bác bỏ ở cả hai | Hai mô hình tương đương → Chọn theo AIC/BIC |
| Bác bỏ ở một chiều | Chọn mô hình không bị bác bỏ |

### 8.5.6. Bảng tổng hợp tiêu chuẩn chọn mô hình

| Tiêu chuẩn | Quy tắc | Ưu điểm | Nhược điểm |
|:---|:---|:---|:---|
| R̄² | Cao hơn tốt hơn | Đơn giản | Không phạt đủ biến thừa |
| AIC | Thấp hơn tốt hơn | Cân bằng phù hợp – tiết kiệm | Chọn mô hình hơi phức tạp |
| BIC | Thấp hơn tốt hơn | Mô hình đơn giản | Có thể quá đơn giản |
| F-test | p-value < α → giữ biến | Chính xác | Chỉ cho mô hình lồng nhau |
| J-test | Kiểm định γ = 0 | So sánh trực tiếp | Phức tạp |
| RESET | p-value < α → sai sót | Phát hiện underfitting | Không chỉ ra biến cụ thể |

## 8.6. QUY TRÌNH THỰC HÀNH CHỌN MÔ HÌNH

| Bước | Hành động | Công cụ |
|:---|:---|:---|
| 1 | Liệt kê biến tiềm năng (cốt lõi, kiểm soát, loại trừ) | Lý thuyết kinh tế |
| 2 | Ước lượng mô hình đầy đủ — kiểm tra dấu, p-value, VIF | OLS |
| 3 | Loại biến không ý nghĩa (p-value lớn nhất trước) | Kiểm định t, F, R̄² |
| 4 | Kiểm tra sai sót đặc tả | Kiểm định RESET |
| 5 | So sánh mô hình ứng viên | AIC, BIC, R̄², F-test, J-test |
| 6 | Kiểm tra giả thiết cổ điển | BP, White, DW, VIF |
| 7 | Kiểm tra khả năng dự báo (nếu có đủ dữ liệu) | RMSE, MAE |

**Lưu ý khi loại biến:** Sau mỗi lần loại, kiểm tra R̄² có giảm nhiều không? Hệ số còn lại có thay đổi lớn không? Dấu có đảo không? Nếu có → cân nhắc giữ lại.

## 8.7. VÍ DỤ ÁP DỤNG

### 8.7.1. Bối cảnh

Nhà nghiên cứu phân tích yếu tố ảnh hưởng đến chi tiêu tiêu dùng (Y, triệu đồng/tháng) của 200 hộ gia đình tại TP.HCM. Các biến tiềm năng: Thu nhập (X₂), Lãi suất (X₃), Quy mô hộ (X₄), Học vấn (X₅), Khu vực (X₆, 1 = thành thị).

### 8.7.2. Kết quả ước lượng

**Mô hình 1 (đầy đủ):**

| Biến | Hệ số | p-value | VIF |
|:---|:---|:---|:---|
| Hằng số | −2,50 | 0,167 | — |
| Thu nhập (X₂) | 0,85 | 0,000 | 1,45 |
| Lãi suất (X₃) | −0,30 | 0,097 | 1,12 |
| Quy mô hộ (X₄) | 0,75 | 0,001 | 1,35 |
| Học vấn (X₅) | 0,15 | 0,135 | 1,28 |
| Khu vực (X₆) | 1,80 | 0,006 | 1,18 |

R² = 0,82, R̄² = 0,81, AIC = 452, BIC = 470

**Mô hình 2 (loại X₃ và X₅):**

| Biến | Hệ số | p-value |
|:---|:---|:---|
| Hằng số | −1,80 | 0,232 |
| Thu nhập (X₂) | 0,88 | 0,000 |
| Quy mô hộ (X₄) | 0,80 | 0,000 |
| Khu vực (X₆) | 2,00 | 0,001 |

R² = 0,81, R̄² = 0,80, AIC = 450, BIC = 464

**Mô hình 3 (chỉ Thu nhập):** R² = 0,74, R̄² = 0,74, AIC = 502, BIC = 510

### 8.7.3. So sánh và lựa chọn

| Tiêu chí | M1 (đầy đủ) | M2 (rút gọn) | M3 (chỉ thu nhập) |
|:---|:---|:---|:---|
| R̄² | 0,81 | **0,80** | 0,74 |
| AIC | 452 | **450** ✓ | 502 |
| BIC | 470 | **464** ✓ | 510 |
| Biến có ý nghĩa (5%) | 3/5 | 3/3 | 1/1 |

**Kiểm định F M2 vs M3:** F = 35,0 > F tới hạn (3,04) → Bác bỏ H₀ → M2 tốt hơn M3.

**Kiểm định RESET M2:** F = 1,85, p-value = 0,140 → Không bác bỏ H₀ → M2 không sai sót.

**Kết luận:** Chọn **Mô hình 2** — cân bằng tốt nhất.

### 8.7.4. Diễn giải mô hình cuối cùng

$$\hat{Y} = -1,80 + 0,88 \times \text{Thu nhập} + 0,80 \times \text{Quy mô hộ} + 2,00 \times \text{Khu vực}$$

- **Thu nhập (0,88):** Tăng 1 triệu → chi tiêu tăng 0,88 triệu (p = 0,000).
- **Quy mô hộ (0,80):** Thêm 1 người → chi tiêu tăng 0,80 triệu (p = 0,000).
- **Khu vực (2,00):** Thành thị chi tiêu hơn nông thôn 2,00 triệu (p = 0,001).
- **R² = 0,81:** Giải thích 81% biến động chi tiêu.

## 8.8. LỖI THƯỜNG GẶP

**Lỗi 1: Chọn mô hình chỉ dựa R² cao nhất.** Sai. R² luôn tăng khi thêm biến. Dùng R̄², AIC, BIC kết hợp.

**Lỗi 2: Loại biến chỉ vì p-value > 0,05.** Chưa đúng. Cần xem xét lý thuyết kinh tế, cỡ mẫu, đa cộng tuyến, vai trò biến kiểm soát.

**Lỗi 3: Không kiểm tra giả thiết sau khi chọn mô hình.** Chưa đủ. Cần kiểm tra VIF, BP, White, DW, BG.

**Lỗi 4: So sánh R² khi biến phụ thuộc khác nhau (Y vs. ln(Y)).** Sai. TSS khác nhau → không so sánh trực tiếp. Dùng AIC, RMSE.

**Lỗi 5: Nhầm RESET chỉ ra biến cụ thể bị bỏ sót.** Sai. RESET chỉ cho biết mô hình bị sai sót, không chỉ ra biến cụ thể.

**Lỗi 6: Loại biến "backward stepwise" mù quáng.** Có thể loại biến kiểm soát quan trọng. Cần kết hợp lý thuyết.

**Lỗi 7: Đưa tất cả biến có sẵn vào để "chắc chắn".** Overfitting. Nguyên tắc parsimony: đơn giản hơn luôn được ưu tiên nếu chất lượng tương đương.

## BÀI TẬP TÌNH HUỐNG THEO NGÀNH

### Tình huống 1 — QUẢN TRỊ KINH DOANH & TÀI CHÍNH: Dự báo doanh thu và định giá

**Phần A — Dự báo doanh thu:**

Công ty FMCG dự báo doanh thu (Y, tỷ đồng/tháng) từ dữ liệu 50 chi nhánh:

| Biến | Hệ số | p-value | VIF |
|:---|:---|:---|:---|
| Quảng cáo (X₂) | 3,5 | 0,002 | 1,80 |
| Giá bán (X₃) | −2,0 | 0,001 | 1,45 |
| Điểm bán (X₄) | 0,8 | 0,000 | 2,50 |
| Khuyến mãi (X₅) | 5,2 | 0,030 | 1,20 |
| Khu vực (X₆) | 1,5 | 0,250 | 1,30 |

R² = 0,88, R̄² = 0,87, AIC = 320, BIC = 335

**Yêu cầu:**
a) Đánh giá mô hình theo Bảng 8-1. Biến nào nên loại?
b) Sau khi loại X₆: R̄² = 0,87, AIC = 318, BIC = 330. So sánh. Nên chọn mô hình nào?
c) Kiểm định RESET: F = 2,10, p-value = 0,13. Diễn giải.

**Phần B — Định giá cổ phiếu:**

Nhà phân tích xây dựng mô hình dự báo giá cổ phiếu từ 80 công ty niêm yết:

| Mô hình | Biến | R² | R̄² | AIC |
|:---|:---|:---|:---|:---|
| M1 | EPS, P/E, Tăng trưởng DT, ROE, Ngành | 0,75 | 0,73 | 680 |
| M2 | EPS, P/E, Tăng trưởng DT, Ngành | 0,74 | 0,73 | 678 |

Giả sử kiểm định F cho H₀: ROE = 0: F = 0,57, p-value = 0,45.

**Yêu cầu:**
d) So sánh M1 và M2 theo AIC, R̄². ROE có nên loại không?
e) Kiểm định F cho kết luận gì? Ngành (p-value = 0,10 ở M2) — nên giữ hay loại? Thảo luận.

### Tình huống 2 — KINH TẾ & KHOA HỌC DỮ LIỆU: Tăng trưởng GDP và giá nhà

**Phần A — Tăng trưởng GDP:**

Dữ liệu bảng 63 tỉnh, 5 năm (2019–2023):

| Biến | Hệ số | p-value | VIF |
|:---|:---|:---|:---|
| Vốn/GDP | 0,12 | 0,000 | 2,10 |
| Lao động đào tạo | 0,08 | 0,015 | 1,80 |
| FDI/GDP | 0,05 | 0,120 | 1,50 |
| PCI | 0,03 | 0,005 | 1,65 |
| Diện tích | −0,01 | 0,850 | 1,10 |

R² = 0,65, R̄² = 0,64, AIC = 1250, BIC = 1280

**Yêu cầu:**
a) Diện tích (p = 0,85) — loại ngay? FDI (p = 0,12) — giữ hay loại? Giải thích.
b) VIF tối đa 2,10 — đa cộng tuyến nghiêm trọng không?
c) Nhà nghiên cứu muốn kiểm tra tương tác PCI × FDI. Đề xuất cách xây dựng mô hình.

**Phần B — Dự báo giá nhà:**

| Mô hình | Biến | R² | R̄² | AIC | BIC |
|:---|:---|:---|:---|:---|:---|
| M1 | Diện tích | 0,65 | 0,65 | 320 | 326 |
| M2 | Diện tích, Số phòng ngủ | 0,72 | 0,71 | 298 | 308 |
| M3 | Diện tích, Số phòng ngủ, Tầng, Quận | 0,80 | 0,79 | 260 | 280 |
| M4 | M3 + Năm xây, Hướng, Ban công | 0,82 | 0,80 | 258 | 290 |

**Yêu cầu:**
d) Mô hình nào tốt nhất theo R̄²? Theo AIC? Theo BIC? Tại sao khác nhau?
e) M3 → M4: R² tăng 0,02 nhưng BIC tăng 10. Nhận xét. Đề xuất mô hình cuối cùng.

## BÀI TẬP

**Bài tập 8.1.** Cho mô hình: Y = β₁ + β₂X₂ + β₃X₃ + β₄X₄ + u, n = 50, RSS = 120, ESS = 380, k = 4.

a) Tính TSS, R², R̄².

b) Thêm X₅, RSS giảm xuống 105, k = 5. Tính R² mới và R̄² mới. Nhận xét.

c) Tính AIC cả hai mô hình (AIC = n × ln(RSS/n) + 2k). Mô hình nào tốt hơn?

**Bài tập 8.2.** Phát biểu đúng hay sai? Giải thích:

a) "R² = 0,95 luôn tốt hơn R² = 0,70."

b) "Nếu RESET bác bỏ H₀, ta biết biến nào bị bỏ sót."

c) "Underfitting nghiêm trọng hơn overfitting."

d) "AIC và BIC luôn chọn cùng mô hình."

**Bài tập 8.3.** Kiểm định F so sánh mô hình đầy đủ (5 biến) và rút gọn (3 biến): RSS\_đầy đủ = 80, RSS\_rút gọn = 110, n = 100, q = 2, k = 5.

a) Tính F. F tới hạn (0,05; 2; 95) ≈ 3,09. Kết luận?

b) Nên chọn mô hình nào?

**Bài tập 8.4.** Kết quả Stata cho mô hình dự báo giá cà phê:

Mô hình 1 (2 biến): RSS = 30,80, n = 50, k = 3, R² = 0,5947, R̄² = 0,5775.

Mô hình 2 (3 biến): RSS = 27,50, n = 50, k = 4, R² = 0,6382, R̄² = 0,6148.

a) Tính AIC cả hai mô hình. So sánh.

b) Kiểm định F cho H₀: hệ số biến thứ 3 = 0. F tới hạn (0,05; 1; 46) ≈ 4,05. Kết luận?

c) Nếu RESET cho M2: F = 1,25, p-value = 0,30. Nhận xét.

**Bài tập 8.5.** (Tư duy phản biện) Sinh viên viết: "Tôi thử 20 biến, mô hình tốt nhất có 15 biến, R² = 0,95."

a) Mô hình có thể gặp vấn đề gì?

b) Nếu 15 biến có VIF trung bình = 8,5, cho thấy vấn đề gì?

c) Đề xuất quy trình chọn mô hình khác.

## CÂU HỎI TRẮC NGHIỆM (Bài 8) — 15 câu

**Câu 1.** Theo nguyên tắc parsimony, khi hai mô hình có chất lượng tương đương, nên chọn:

a) Mô hình có R² cao hơn. b) Mô hình có nhiều biến hơn. c) Mô hình đơn giản hơn. d) Mô hình có hệ số chặn lớn hơn.

**Đáp án: c**

**Câu 2.** Sai số do thiếu biến xảy ra khi:

a) Đưa vào biến không liên quan. b) Bỏ sót biến tương quan với cả Y và biến độc lập. c) Có quá nhiều biến. d) Sai số không chuẩn.

**Đáp án: b**

**Câu 3.** Kiểm định RESET kiểm tra:

a) Đa cộng tuyến. b) Phương sai thay đổi. c) Sai sót đặc tả mô hình. d) Tự tương quan.

**Đáp án: c**

**Câu 4.** Trong kiểm định RESET, nếu F tính > F tới hạn:

a) Mô hình đúng dạng. b) Mô hình bị sai sót → cần sửa. c) Loại biến p-value cao nhất. d) Thêm biến giả.

**Đáp án: b**

**Câu 5.** AIC và BIC khác nhau ở:

a) AIC phạt nặng hơn. b) BIC phạt nặng hơn (khi n > 7). c) AIC chỉ cho dữ liệu chéo. d) Không khác biệt.

**Đáp án: b**

**Câu 6.** Mô hình A: AIC = 520. Mô hình B: AIC = 535. Theo AIC:

a) A tốt hơn. b) B tốt hơn. c) Tương đương. d) Không kết luận.

**Đáp án: a**

**Câu 7.** Kiểm định F so sánh mô hình lồng nhau có H₀:

a) Tất cả hệ số = 0. b) Hệ số biến bị loại đều = 0. c) R² = 0. d) Phương sai thay đổi.

**Đáp án: b**

**Câu 8.** So sánh mô hình Y vs. ln(Y), không nên dùng:

a) AIC. b) BIC. c) R² hoặc R̄². d) RMSE.

**Đáp án: c**

**Câu 9.** Overfitting là:

a) Quá đơn giản. b) Quá phức tạp, đưa biến không liên quan. c) Sai số không chuẩn. d) Tương quan mạnh.

**Đáp án: b**

**Câu 10.** Hậu quả underfitting:

a) Không chệch nhưng kém hiệu quả. b) Ước lượng bị chệch. c) R² = 0. d) Không hậu quả.

**Đáp án: b**

**Câu 11.** Bước đầu tiên chọn mô hình:

a) Chạy hồi quy tất cả biến. b) Xác định biến từ lý thuyết. c) Loại p-value > 0,05. d) Tính AIC, BIC.

**Đáp án: b**

**Câu 12.** M1: R² = 0,80, R̄² = 0,78, AIC = 400. M2: R² = 0,82, R̄² = 0,77, AIC = 410. Chọn:

a) M1. b) M2. c) Tương đương. d) Không đủ thông tin.

**Đáp án: a**

**Câu 13.** RESET: F = 1,20, p-value = 0,31 (α = 5%). Kết luận:

a) Sai sót. b) Không đủ bằng chứng sai sót. c) X₂ không ý nghĩa. d) Đa cộng tuyến.

**Đáp án: b**

**Câu 14.** VIF > 10 cho thấy:

a) Không ý nghĩa thống kê. b) Đa cộng tuyến nghiêm trọng. c) Sai sót đặc tả. d) Phương sai thay đổi.

**Đáp án: b**

**Câu 15.** ĐÚNG nhất về chọn mô hình:

a) Luôn chọn R² cao nhất. b) Loại ngay p-value > 0,05. c) Kết hợp lý thuyết, tiêu chí thống kê (AIC, BIC, R̄²) và kiểm định. d) Nhiều biến càng tốt.

**Đáp án: c**

## BẢNG TÓM TẮT CÔNG THỨC CHÍNH

| Công thức | Biểu thức |
|:---|:---|
| R̄² | $\bar{R}^2 = 1 - (1-R^2)\frac{n-1}{n-k}$ |
| AIC | $AIC = n \cdot \ln(RSS/n) + 2k$ |
| BIC | $BIC = n \cdot \ln(RSS/n) + k \cdot \ln(n)$ |
| F (Wald) | $F = \frac{(RSS_r - RSS_u)/q}{RSS_u/(n-k)}$ |
| RESET | $F = \frac{(RSS_r - RSS_f)/q}{RSS_f/(n-k-q)}$ |
| OVB | $E(\hat{\alpha}_2) = \beta_2 + \beta_3 \cdot \frac{Cov(X_2,X_3)}{Var(X_2)}$ |

| Tiêu chí | Quy tắc |
|:---|:---|
| R̄² | Cao hơn tốt hơn |
| AIC | Thấp hơn tốt hơn |
| BIC | Thấp hơn tốt hơn |
| F-test (lồng nhau) | p-value < α → giữ biến |
| RESET | p-value < α → mô hình sai sót |
| VIF > 10 | Đa cộng tuyến nghiêm trọng |

---

*Tài liệu tham khảo: Gujarati & Porter (2009), Wooldridge (2016), Stock & Watson (2020).*

