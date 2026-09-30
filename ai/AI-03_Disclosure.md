# [AI-03] Biểu mẫu Khai báo Sử dụng AI — HW01-AI

Khoa Công nghệ Thông tin (FIT) – Trường Đại học Khoa học Tự nhiên (HCMUS) · CS423 / CSC13003 – Kiểm chứng Phần mềm (AI-augmented · 2026)

## 1. Thông tin môn học và sinh viên

| Mục              | Giá trị                                                                   |
| ---------------- | ------------------------------------------------------------------------- |
| Môn học          | CS423 / CSC13003 – Kiểm chứng Phần mềm                                    |
| Mã bài tập       | HW01-AI                                                                   |
| Tên bài tập      | HW01 — QA/QC Jobs · 20 Defects · Test a Physical Product                  |
| Cấp độ AI (1–5)  | Cấp 4 — AI hỗ trợ sản xuất (thoả thuận AI mục 4: áp dụng cho HW#01–HW#06) |
| Ngày             | 30/9/2026                                                                 |
| Họ tên sinh viên | NGUYỄN PHÚ DINH                                                           |
| MSSV             | 23120031                                                                  |

## 2. Câu hỏi khai báo

### 1. Công cụ AI đã dùng

- Claude Code (tiện ích VSCode), model Claude Sonnet 5.5 — Anthropic.
- ChatGPT bản web, model GPT 5.6, có bật web search — OpenAI.
- Codex, model GPT-5 — OpenAI, chỉ dùng để kiểm chứng độc lập 3 lỗi của mindmap (prompt log Mục 17).

### 2. Giai đoạn nào của bài tập có dùng AI

- [x] brainstorm
- [x] outline (gợi ý cấu trúc thư mục, dựng khung file)
- [x] viết nháp (mô tả công việc, danh sách lỗi phần mềm, mindmap, test case)
- [x] phản hồi (kiểm tra, đối chiếu kết quả)
- [x] sửa chữa
- [x] code (script Python dựng ảnh mindmap và điền file Excel theo template)
- [x] phân tích dữ liệu (đối chiếu điểm CVSS với NVD, kiểm tra link)
- [x] thiết kế đồ hoạ (ảnh mindmap)
- [ ] khác

### 3. Prompt / nhiệm vụ chính cho AI

Các prompt quan trọng nhất (nguyên văn); danh sách đầy đủ có giờ chính xác ở Phụ lục A: [prompt_log.md](prompt_log.md).

1. ChatGPT Web, 00:08 30/09/2026 (Yêu cầu 2, prompt đầu): "Find 20 software defects publicized between 2022 and 2026. Mandatory: ≥ 5 defects related to AI/LLM (hallucination, prompt injection, bias). Each defect: source link, description, severity, consequences, solution." với yêu cầu này có nên bật web search trên chatgpt
2. ChatGPT Web, 00:08 30/09/2026 (Yêu cầu 2, prompt tìm 5 lỗi AI): "tìm 5 software defects liên quan đến AI/LLM được công bố trong giai đoạn 2022 – 2026 (thuộc các dạng: hallucination, prompt injection, model bias). với mỗi lỗi, trình bày đầy đủ các mục: Tên sự cố/lỗ hỏng (Kèm mã CVE hoặc tên tổ chức bị ảnh hưởng), source link, description: Chi tiết nguyên nhân kỹ thuật gây ra lỗi, severity: đánh giá mức độ nghiêm trọng ow/edium/high/critical hoặc CVSS nếu có), consequences: hậu quả trực tiếp đối với người dùng hoặc hệ thống, solution: bản vá hoặc giải pháp đã được áp dụng, yêu cầu: trình bày chi tiết, chuyên sâu về mặt kỹ thuật phần mềm."
3. Claude Code, 08:07:01 30/09/2026 (mindmap G9.1): "tôi đã xóa phần phụ lục, mục req2 xem như đã xong, giờ hãy tạo mindmap QA/QC"
4. Claude Code, 09:13:39 30/09/2026 (Yêu cầu 3, G9.3): "Theo đề bài thì có vẻ nên là bạn tự tạo test case, sau đó tôi sẽ kiểm tra lại và thêm edge case, video tôi sẽ thêm sau khi có test cases. thiết bị và ảnh thiết bị tôi đã thêm vào sẵn"

### 4. Phần cụ thể AI đóng góp

**Yêu cầu 1 (thị trường việc làm và mindmap)**

- AI (Claude) trích và tóm tắt mô tả công việc, kỹ năng yêu cầu của 10 tin từ nội dung trang tin; soạn nháp 10 đoạn AI Impact Analysis; dựng khung `jobs.md`.
- AI tạo mindmap QA/QC (ảnh PNG và mã Mermaid). Claude và Codex đối chiếu 3 lỗi với giáo trình ISTQB.
- Sinh viên tự tìm 10 tin, tự chụp ảnh màn hình có tên tài khoản, chọn 3 tin yêu cầu AI, chốt mức lương và đơn vị, chép nguyên văn mô tả tin 2, quyết định nội dung cuối.

**Yêu cầu 2 (20 lỗi phần mềm)**

- ChatGPT tìm và tổng hợp 20 lỗi (5 lỗi AI/LLM và 15 lỗi khác).
- Claude đối chiếu điểm CVSS với NVD, kiểm tra link, viết mục "chỗ AI thiên lệch" dựa trên phát hiện của sinh viên.
- Sinh viên phát hiện chỗ ChatGPT thiên lệch ở case 4 (Air Canada) và quyết định giữ case này trong danh sách.

**Yêu cầu 3 (thiết bị vật lý)**

- AI (Claude) tạo bản gốc 15 test case cho quạt Kenfan B4 (lưu nguyên ở `ai_testcases_original.md`), dựng khung Excel theo template, điền sheet Test Case Checklist, đồng bộ dữ liệu giữa Excel và Markdown.
- Sinh viên thay 01-005, 02-005 và thay 03-005 bằng 04-001 (edge case AI bỏ sót); tự thực thi 5 test case, tự quay 5 video có giọng nói, tự ghi kết quả thực tế; tự chụp ảnh thiết bị cùng thẻ sinh viên.
- Bug report: theo quy định 100% do sinh viên viết. Trong lượt làm việc lúc 10:34:52 30/09/2026 AI đã điền nháp phần tóm tắt và các bước tái hiện bug 01-005 trong file Excel; khi kiểm tra ở lượt 11:01:41 30/09/2026 phần này bị phát hiện vi phạm quy định và đã được gỡ bỏ. Sinh viên tự viết mô tả bug.

**Phần AI Critique:** AI soạn bản nháp 278 từ dựa trên các bằng chứng đã kiểm chứng (mục 5 của `report/HW01_report.md`).

**AI KHÔNG đóng góp vào:** ảnh thiết bị và thẻ sinh viên (do sinh viên chụp; AI chỉ đọc ảnh, xem AI-05), video thực thi, ảnh chụp màn hình tin tuyển dụng, kết quả thực tế (Actual) của các test case, mô tả bug và phần còn lại của báo cáo chính khi hoàn thành.

### 5. Cách tôi rà soát / chỉnh sửa / xác minh đầu ra AI

- **Đối chiếu tài liệu chính thức:** giáo trình ISTQB CTFL v4.0.1 (tìm ra 3 lỗi mindmap: test level, use case testing, monitoring & control) và điểm CVSS của các CVE tra trên NVD.
- **Kiểm chứng độc lập:** nhờ Codex đọc lại mindmap, đối chiếu giáo trình và trích dẫn từng lỗi (Mục 17).
- **Kiểm tra nguồn:** mở các link nguồn của 20 lỗi trên trình duyệt (sinh viên xác nhận mở được).
- **Chạy trên thiết bị thật:** thực thi 5 test case và quay video; so bản gốc của AI với danh sách cuối để tìm edge case AI bỏ sót.
- **Kiểm tra chất lượng test case:** dùng sheet Test Case Checklist.
- **Kiểm tra chéo dữ liệu:** đối chiếu trực tiếp nội dung Excel với Markdown.

### 6. Trích dẫn (phong cách IEEE)

[1] Anthropic, "Claude Code (Claude Sonnet 5.5)" [Large language model], 2026. [Online]. Available: https://claude.ai

[2] OpenAI, "ChatGPT (GPT 5.6)" [Large language model], 2026. [Online]. Available: https://chatgpt.com

[3] OpenAI, "Codex (GPT-5)" [Large language model], 2026. [Online]. Available: https://openai.com

[4] ISTQB, "Certified Tester Foundation Level Syllabus v4.0.1," Sep. 2024. [Online]. Available: https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf

[5] NIST, "National Vulnerability Database," 2026. [Online]. Available: https://nvd.nist.gov (accessed Sep. 30, 2026).

[6] Moffatt v. Air Canada, 2024 BCCRT 149 (CanLII). [Online]. Available: https://www.canlii.org/en/bc/bccrt/doc/2024/2024bccrt149/2024bccrt149.html

## 3. Cam đoan trung thực

Bằng việc ký tên dưới đây, tôi cam đoan thông tin khai báo ở trên là chính xác và đầy đủ. Tôi hiểu rằng việc không khai báo hoặc khai báo sai lệch về việc dùng AI sẽ bị coi là vi phạm liêm chính học thuật và có thể dẫn đến điểm 0 cho bài tập cùng việc bị chuyển lên hội đồng kỷ luật.

## Chữ ký

| Mục                       | Giá trị                                                                                                      |
| ------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Họ tên sinh viên (in hoa) | NGUYỄN PHÚ DINH                                                                                              |
| MSSV                      | 23120031                                                                                                     |
| Lớp / Khoá                | CQ2023/3                                                                                                     |
| Môn học                   | CS423 / CSC13003 – Kiểm chứng Phần mềm                                                                       |
| Giảng viên                | TS. Lâm Quang Vũ / TS. Trần Duy Hoàng / ThS. Trần Thị Bích Hạnh / ThS. Trương Phước Lộc / ThS. Hồ Tuấn Thanh |
| Ngày                      | 30/9/2026                                                                                                    |
| Chữ ký                    | Dinh                                                                                                         |
