# Phiên Claude Code 28/09/2026 — đọc chính sách bài tập và yêu cầu HW01

Công cụ: Claude Code (VSCode extension), model Claude Sonnet 5.5. Xuất tự động từ file transcript của Claude Code: chỉ gồm lời nhắn của sinh viên và câu trả lời bằng chữ của AI; không gồm nội dung gọi công cụ (đọc/ghi file, lệnh shell). Giờ theo múi giờ máy (UTC+7). Phiên chính vẫn đang diễn ra nên cần xuất lại trước khi nộp.


---

### [23:19:38 28/09/2026] SINH VIÊN

kiem tra @Homeworks/___2026.Homework.Policies.md va tom tat lai cho toi noi dung


---

### [23:19:52 28/09/2026] AI (Claude)

Tóm tắt [___2026.Homework.Policies.md](Homeworks/___2026.Homework.Policies.md), quy định làm bài tập môn Kiểm thử phần mềm (Software Testing) 2026:

## 1. Nguyên tắc chung
- **Làm cá nhân:** Mọi bài tập đều là bài cá nhân. Bạn vẫn được thảo luận với giảng viên, trợ giảng, bạn học và được dùng AI, miễn là dùng có trách nhiệm.
- **Tiêu chí chính:** Dùng AI thông minh, hiệu quả và làm kiểm thử đúng quy trình, đúng kỹ thuật. **Số lượng test case và số bug tìm được** là căn cứ để phân loại điểm giữa các sinh viên.
- **Khai báo AI:** Bắt buộc khai báo việc dùng AI theo tài liệu "AI Usage Guideline" và hướng dẫn của giảng viên.

## 2. Định dạng file
- Chỉ nộp **file dạng text**. Khuyến khích dùng **Markdown**, LaTeX cũng được.
- Nếu trước đây bạn dùng **Word** thì phải chuyển sang Markdown.
- Nếu dùng **Excel** thì vẫn làm trên Excel được, nhưng phải chép các bảng tổng hợp vào file Markdown.
- Nếu trình bày bằng **PowerPoint** thì nên chuyển sang Markdown ở chế độ trình chiếu.
- Ngoài file gốc, phải nộp thêm **bản PDF** (Save-As-PDF).

## 3. Quản lý phiên bản bằng Git
- Bắt buộc dùng Git (GitHub, Bitbucket hoặc GitLab).
- **Mỗi bước** trong từng yêu cầu phải có một commit với message rõ ràng.
- Nộp kèm **git commit log**.

## 4. Làm việc nhóm (bài tập đồ án)
- Phần việc của mỗi người không được trùng với thành viên khác.
- Phải cân bằng độ khó giữa các thành viên. Chọn việc quá dễ sẽ **bị giới hạn điểm tối đa**, dù làm xong hết.
- **Review chéo** bài của thành viên khác. Review phải có góp ý mang tính xây dựng; review chỉ khen sẽ không được đánh giá cao.

## 5. Tự chấm điểm
- Mỗi bài có rubric, sinh viên phải tự chấm điểm cho bài của mình.
- **Tên file nộp:** `StudentID_ExerciseID_SelfAssessedGrade.zip`, trong đó điểm tự chấm là **3 chữ số từ 000 đến 100** (ví dụ `21120001_HW01_085.zip`).
- Khi giảng viên chấm, một số bài hoặc phần sẽ có trọng số cao hơn.

## 6. Nộp bài
- Nộp qua **Moodle**.
- **Không nhận bài nộp trễ.** Chỉ ngoại lệ khi có lý do nghiêm trọng (sức khỏe, gia đình), và phải email cho giảng viên kèm minh chứng đầy đủ.
- Tối đa **20 file, mỗi file không quá 20 MB**. Nếu vượt thì dùng tính năng chia nhỏ file nén (split-and-zip).
- ⚠️ Lạm dụng hoặc phụ thuộc quá nhiều vào **link online** trong bài nộp sẽ bị **0 điểm**.

## 7. Tuân thủ và liêm chính học thuật
- Vi phạm **bất kỳ** quy định nộp bài nào sẽ bị **0 điểm** cho bài đó.
- Vi phạm quy định chống gian lận (Anti-Cheat) sẽ bị xử lý như **gian lận học thuật**.

## 8. Liên hệ
Hỏi qua Diễn đàn thảo luận (Discussion Forum) trên Moodle hoặc email: lqvu, ttbhanh, tdhoang, tploc, htthanh (đều có đuôi @fit.hcmus.edu.vn).

---

**Những lỗi dễ bị 0 điểm nhất:** đặt sai tên file, thiếu bản PDF, không có commit log, dùng quá nhiều link online, hoặc nộp trễ.


---

### [23:22:44 28/09/2026] SINH VIÊN

hien tai toi dang can lam @Homeworks/HW01/2026.HW01.Jobs.Defects.PhysicalProduct_En.docx  tao mot file excel/markdown co checklist de toi check cac thu can lam


---

### [23:23:52 28/09/2026] AI (Claude)

Mình đã tạo file checklist cho HW01: [HW01_Checklist.md](HW01_Checklist.md). Mình chọn Markdown vì Policy khuyến khích nộp bằng Markdown.

File gồm 7 phần:
0. **Chuẩn bị:** tạo Git repo, tạo prompt log, lấy các template AI, tạo tài khoản FIT Mantis, tạo file Excel.
1. **R1: 10 tin tuyển dụng.** Có sẵn bảng 10 dòng để tick từng mục (link, screenshot có username, JD, kỹ năng, lương, AI Impact). Phần này còn có mindmap QA/QC: bạn tìm 3 lỗi trong mindmap AI vẽ.
2. **R2: 20 lỗi phần mềm 2022–2026.** Có bảng 20 dòng, yêu cầu ít nhất 5 lỗi liên quan AI, và tìm 1 chỗ AI bị thiên lệch hoặc bịa khi giải thích lỗi.
3. **R3: thiết bị vật lý.** Gồm ảnh thiết bị chụp cùng thẻ sinh viên, 15 test case, ít nhất 3 edge case mà AI không tìm ra, và ít nhất 5 video (mỗi video ≤ 60 giây, có giọng thuyết minh của bạn).
4. **AI Protocol (15 điểm):** Audit Report 5 mục, AI Critique 200–300 từ, Disclosure, các form AI-03 và AI-05.
5–6. **Report, tự chấm và đóng gói:** bảng rubric để tự chấm, danh sách các file cần có trong .zip, cách đặt tên file.
7. **Chuẩn bị vấn đáp.**

**Một số chỗ trong đề không khớp nhau**, nên hỏi lại giảng viên (mình đã ghi ở cuối file):
- **Điểm R3:** phần mô tả ghi 40 điểm, nhưng rubric ghi 25. Rubric cộng lại đúng 100 nên nhiều khả năng rubric là đúng.
- **Tên file:** đề ghi `StudentID_HW01_AI_<grade>.zip`, còn Policy chung ghi `StudentID_ExerciseID_SelfAssessedGrade.zip`.
- **Mantis:** đề yêu cầu screenshot bug trên FIT Mantis, dù HW01 là test thiết bị vật lý.

Nếu bạn cần thêm bản Excel (sheet Test Cases, Checklist, Test Summary Report mà đề yêu cầu nộp), mình có thể tạo luôn.
