\newpage

# Giới thiệu về tài liệu {#sec:gioi-thieu}

## Lời nói đầu

Tài liệu học phần *Kinh tế lượng* được biên soạn nhằm cung cấp cho sinh viên các công cụ cơ bản của phân tích kinh tế lượng. Phần này giới thiệu các phương pháp chuẩn để ước lượng các mối quan hệ giữa các biến kinh tế từ dữ liệu thực tế, và kiểm định các giả thuyết thống kê về các mối quan hệ đó.

Sinh viên sẽ được học cách sử dụng các mô hình, dữ liệu và phép phân tích phù hợp để mô tả thế giới thực và góp phần vào những cuộc thảo luận chính sách. Tài liệu cũng giới thiệu về sức mạnh của các phương pháp phân tích định lượng cũng như những hạn chế cần lưu ý khi áp dụng. Trọng tâm là định dạng, ước lượng, kiểm định các mô hình kinh tế lượng và thảo luận chính sách từ các kết quả phân tích định lượng. Học viên cũng sẽ được học cách tiến hành các nghiên cứu thực nghiệm thông qua dự án học phần.

Tài liệu được biên soạn dựa trên các nguồn tài liệu kinh tế lượng uy tín trong và ngoài nước, bao gồm Gujarati và Porter (2009), Stock và Watson (2020), Wooldridge (2016), cùng với các dữ liệu cập nhật từ Tổng cục Thống kê Việt Nam và các tổ chức quốc tế như Ngân hàng Thế giới (World Bank), Ngân hàng Phát triển Châu Á (ADB) và Quỹ Tiền tệ Quốc tế (IMF).

## Mục đích và yêu cầu

Sau khi hoàn thành học phần này, sinh viên sẽ đạt được các năng lực sau:

**Về kiến thức:** Hiểu các khái niệm, thuật ngữ và lý thuyết nền tảng trong kinh tế lượng, bao gồm hồi quy hai biến, hồi quy đa biến, biến giả, đa cộng tuyến, phương sai thay đổi, tự tương quan và các tiêu chí chọn mô hình.

**Về kỹ năng:** Sử dụng được các kỹ thuật ước lượng mô hình hồi quy tuyến tính; phân tích tính đúng đắn về mặt kỹ thuật cũng như kinh tế của mô hình; đọc và diễn giải kết quả từ các phần mềm chuyên dụng.

**Về vận dụng:** Vận dụng được các công cụ phân tích định lượng vào các vấn đề kinh tế, tài chính, quản trị kinh doanh và hoạch định chính sách trên cơ sở sử dụng phần mềm chuyên dùng (EViews, Stata, R, Excel) với cơ sở dữ liệu thực tế.

## Kiến thức tiền đề

Học phần đòi hỏi học phần tiền đề là *Xác suất thống kê* (STA1101). Sinh viên cần nắm vững các kiến thức sau trước khi bắt đầu học phần này:

- Các đại lượng thống kê cơ bản: trung bình, phương sai, độ lệch chuẩn.
- Phân phối xác suất: phân phối chuẩn, phân phối $t$-Student, phân phối $F$, phân phối $\chi^2$.
- Ước lượng tham số: ước lượng điểm và khoảng tin cậy.
- Kiểm định giả thuyết: giả thuyết không ($H_0$), giả thuyết đối ($H_1$), mức ý nghĩa, sai lầm loại I và loại II.
- Các phép biến đổi đại số cơ bản: tổng, tích, bình phương, logarit.

## Cấu trúc tài liệu

Tài liệu gồm 8 bài học và các phụ lục, được sắp xếp theo trình tự từ cơ bản đến nâng cao:

**Bài 1 — Tổng quan về kinh tế lượng:** Giới thiệu định nghĩa, lịch sử, phân loại dữ liệu, quy trình nghiên cứu và các phần mềm chuyên dụng. Bài này đặt nền tảng cho toàn bộ khóa học.

**Bài 2 — Hồi quy hai biến:** Trình bày mô hình hồi quy đơn giản nhất với một biến phụ thuộc và một biến độc lập. Sinh viên sẽ học phương pháp bình phương nhỏ nhất (OLS), hệ số xác định $R^2$, kiểm định $t$ và $F$, khoảng tin cậy, dự báo, và các dạng hàm logarit. Bài này cũng giới thiệu vấn đề chuyển đổi đơn vị đo và nguyên tắc "tương quan không có nghĩa là nhân quả."

**Bài 3 — Mô hình hồi quy đa biến:** Mở rộng hồi quy hai biến lên nhiều biến độc lập, giới thiệu khái niệm hệ số hồi quy riêng (*ceteris paribus*), kiểm định $F$ tổng thể, và hiện tượng đa cộng tuyến ở mức cơ bản.

**Bài 4 — Hồi quy với biến giả:** Hướng dẫn cách đưa biến định tính vào mô hình hồi quy thông qua kỹ thuật biến giả (dummy variable), bao gồm biến giả cho hai thuộc tính và nhiều thuộc tính, biến tương tác, kiểm định Chow, phân tích mùa vụ, và phương pháp Difference-in-Differences (DiD).

**Bài 5 — Đa cộng tuyến:** Phân tích hiện tượng tương quan cao giữa các biến độc lập, nguyên nhân, hậu quả, cách phát hiện (hệ số tương quan cặp, VIF, hồi quy phụ) và các biện pháp khắc phục.

**Bài 6 — Phương sai sai số thay đổi (Heteroskedasticity):** Trình bày hiện tượng phương sai của sai số không đổi theo các mức giá trị của biến độc lập, cách phát hiện (đồ thị phần dư, kiểm định Breusch–Pagan, kiểm định White) và khắc phục (ước lượng sai số chuẩn vững — robust standard errors, biến đổi dữ liệu, WLS).

**Bài 7 — Hiện tượng tự tương quan (Autocorrelation):** Phân tích hiện tượng tương quan giữa các sai số liên tiếp trong dữ liệu chuỗi thời gian, cách phát hiện (đồ thị phần dư, thống kê Durbin–Watson, kiểm định Breusch–Godfrey) và khắc phục (phương pháp Newey–West, Cochrane–Orcutt, GLS).

**Bài 8 — Chọn mô hình và kiểm định chọn mô hình:** Giới thiệu các tiêu chí chọn mô hình (Adjusted $R^2$, AIC, BIC), kiểm định thừa biến (Wald test), kiểm định thiếu biến (RESET test của Ramsey), và các nguyên tắc thực hành khi xây dựng mô hình.

**Phụ lục A — Tóm tắt nhanh các bài:** Tổng hợp các khái niệm, công thức và kết luận chính của từng bài để phục vụ ôn tập.

**Phụ lục B — Các bảng tra thống kê:** Cung cấp bảng tra phân phối chuẩn ($Z$), $t$-Student, $F$, $\chi^2$, Durbin–Watson và các giá trị thường dùng.

## Nội dung và cách tiếp cận

Đối với mỗi bài học, người học nên tuân theo trình tự học tập sau:

**Trước khi đến lớp:** Đọc mục tiêu học tập và tóm tắt bài học để nắm được nội dung chính. Đọc qua toàn bộ nội dung bài học, ghi chú các điểm chưa hiểu.

**Trong giờ học:** Nghe giảng, trao đổi với giảng viên về các điểm chưa rõ. Thực hành trên phần mềm theo hướng dẫn.

**Sau giờ học:** Trả lời các câu hỏi ôn tập cuối mỗi mục trong bài học. Làm các bài tập ứng dụng và bài tập tình huống. Thực hành chạy hồi quy trên phần mềm với dữ liệu thực tế.

Mỗi bài học được cấu trúc theo các thành phần sau: **Mục tiêu học tập** liệt kê những năng lực cụ thể mà sinh viên cần đạt được sau khi hoàn thành bài. **Tóm tắt** cung cấp cái nhìn tổng quan về nội dung chính. **Thuật ngữ** liệt kê các thuật ngữ chuyên ngành kèm phiên dịch. **Nội dung lý thuyết** trình bày chi tiết các khái niệm, công thức và quy trình. **Ví dụ minh họa** áp dụng lý thuyết vào các tình huống thực tế tại Việt Nam. **Hướng dẫn thực hành** cung cấp hướng dẫn từng bước trên các phần mềm. **Các lỗi thường gặp** cảnh báo những sai lầm phổ biến. **Bài tập ứng dụng** bao gồm bài tập cơ bản và bài tập tình huống theo ngành. **Câu hỏi trắc nghiệm** giúp kiểm tra nhanh mức độ nắm vững kiến thức.

Tài liệu sử dụng bốn phần mềm chính trong suốt học phần: **Excel** cho phân tích cơ bản và trực quan hóa dữ liệu; **Stata** cho hồi quy đa biến và dữ liệu bảng; **EViews** cho phân tích chuỗi thời gian; **R** cho phân tích nâng cao với hệ sinh thái packages phong phú. Trong đó, R là phần mềm mã nguồn mở miễn phí, phù hợp cho nghiên cứu học thuật và phân tích dữ liệu lớn.

## Phương pháp đánh giá

**Điểm quá trình (30%):** Bao gồm đánh giá chuyên cần (điểm danh), đánh giá bài tập (assignments), đánh giá thuyết trình (oral presentation) và đánh giá làm việc nhóm (teamwork assessment).

**Điểm giữa kỳ (20%):** Đánh giá bài tập (assignments).

**Điểm thi cuối kỳ (50%):** Đánh giá bài tập (assignments).

## Quy ước trình bày trong tài liệu

Để đảm bảo tính nhất quán, tài liệu tuân theo các quy ước trình bày sau:

**Về đánh số:** Các công thức được đánh số liên tục theo dạng (@eq:ten-cong-thuc). Các bảng dữ liệu được đánh số theo dạng **Bảng X-Y** (trong đó X là số bài, Y là số thứ tự bảng trong bài), với tên bảng đặt ở phía trên. Các hình minh họa được đánh số theo dạng **Hình X-Y**, với chú thích đặt ở phía dưới. Các ví dụ được đánh số liên tục theo bài, ví dụ: **Ví dụ 1-1**, **Ví dụ 2-3**.

**Về loại bảng:** Chỉ tạo bảng cho dữ liệu số liệu và bảng thuật ngữ. Các nội dung lý thuyết (quy trình, so sánh, phân loại) được trình bày dưới dạng đoạn văn hoặc danh sách đánh số, không tạo bảng.

**Về trích dẫn:** Tất cả trích dẫn trong văn bản tuân thủ APA7 (tác giả, năm). Danh mục tài liệu tham khảo được liệt kê đầy đủ cuối mỗi bài và tổng hợp ở cuối tài liệu.

**Về phần mềm:** Khi giới thiệu kết quả từ phần mềm (Excel, Stata, EViews, R), tên ô kết quả được giải thích kèm giá trị mẫu để sinh viên dễ dàng đối chiếu.

**Về đơn vị tiền tệ:** Tất cả các ví dụ và bài tập sử dụng đơn vị tiền tệ Việt Nam (đồng, nghìn đồng, triệu đồng, tỷ đồng) trừ khi có ghi chú khác. Khi sử dụng dữ liệu quốc tế, đơn vị được quy đổi hoặc ghi rõ.

## Tài liệu tham khảo chính của học phần

Gujarati, D. N., & Porter, D. C. (2009). *Basic econometrics* (5th ed.). McGraw-Hill.

Stock, J. H., & Watson, M. W. (2020). *Introduction to econometrics* (4th ed.). Pearson.

Wooldridge, J. M. (2016). *Introductory econometrics: A modern approach* (6th ed.). Cengage Learning.
