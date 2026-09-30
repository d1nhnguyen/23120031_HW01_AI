# [AI-02] AI Audit Report — HW01-AI

Khoa Công nghệ Thông tin (FIT) – Trường Đại học Khoa học Tự nhiên (HCMUS) · CS423 / CSC13003 – Kiểm chứng Phần mềm (AI-augmented · 2026)

> **Trạng thái:** bản nháp do AI soạn từ prompt log và transcript. Sinh viên phải rà soát từng verdict, lý do và bản sửa, sửa lại theo nhận định của mình, rồi mới ký. Các mục `[SV XÁC NHẬN]` và `[TỰ ĐIỀN]` là phần sinh viên phải hoàn thành.

## 1. Thông tin sinh viên

| Mục | Giá trị |
|---|---|
| Họ tên sinh viên (in hoa) | NGUYỄN PHÚ DINH |
| MSSV | 23120031 |
| Lớp / Khoá | `[TỰ ĐIỀN]` |
| Mã bài tập | HW01-AI |
| Ngày làm bài | 28/09/2026 – 30/09/2026 |
| Công cụ AI đã dùng | Claude Code (Claude Sonnet 5.5); ChatGPT Web (GPT 5.6); Codex (GPT-5, chỉ dùng để kiểm chứng) |
| Có dùng AI | [x] Có [ ] Không |

Nguồn bằng chứng: [prompt_log.md](prompt_log.md) (giờ chính xác từng lần hỏi) và thư mục [transcripts/](transcripts/) (nguyên văn lời nhắn và câu trả lời bằng chữ của Claude).

## 2. Tổng quan các artifact do AI sinh

| # | Artifact | Công cụ | Verdict |
|---|---|---|---|
| 1 | Mindmap QA/QC (G9.1) | Claude Code | INCOMPLETE |
| 2 | 5 lỗi AI/LLM (Yêu cầu 2) | ChatGPT Web | INCOMPLETE |
| 3 | 15 lỗi phần mềm còn lại (Yêu cầu 2) | ChatGPT Web | INCOMPLETE |
| 4 | Mục "chỗ AI thiên lệch" (Phần C của defects.md) | Claude Code | VALID |
| 5 | Mô tả công việc và kỹ năng yêu cầu của 10 tin tuyển dụng (Yêu cầu 1) | Claude Code | INCOMPLETE |
| 6 | AI Impact Analysis của 10 tin (Yêu cầu 1) | Claude Code | INCOMPLETE (tạm) |
| 7 | 15 test case cho quạt Kenfan B4 (Yêu cầu 3, G9.3) | Claude Code | INCOMPLETE |
| 8 | Điền sheet Test Case Checklist (Yêu cầu 3) | Claude Code | VALID (tạm) |
| 9 | Bản nháp mô tả bug 01-005 (đã gỡ) | Claude Code | INVALID |
| 10 | Bản nháp AI Critique | Claude Code | INCOMPLETE (tạm) |

Không audit: cấu trúc thư mục, các khung Markdown/Excel dựng sẵn, đồng bộ dữ liệu giữa Excel và Markdown (không phải nội dung kiểm thử).

## 3. Chi tiết audit — mỗi artifact 5 mục

### Artifact #1 — Mindmap QA/QC (G9.1)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 08:07:01 30/09/2026 · Prompt: "tôi đã xóa phần phụ lục, mục req2 xem như đã xong, giờ hãy tạo mindmap QA/QC" |
| (2) Output AI | Ảnh [qa-qc-roles.png](../req1-jobs/mindmap/qa-qc-roles.png) và mã Mermaid nguyên văn ở mục 1 của [qa-qc-roles.md](../req1-jobs/mindmap/qa-qc-roles.md); lời giải thích của AI: [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md) (mốc 08:07:01 30/09/2026). |
| (3) Verdict | INCOMPLETE (chấp nhận sau khi sửa) |
| (4) Lý do | Đối chiếu với ISTQB CTFL v4.0.1, có 3 lỗi chính. (a) Test Levels chỉ có 4 mức, trong khi §2.2.1 (tr. 28–29) nêu 5 mức và tách component integration khỏi system integration: INVALID về nội dung. (b) "Use case testing" nằm trong black-box, trong khi §4.2 chỉ có 4 kỹ thuật và phụ lục thay đổi (tr. 75) ghi use case testing đã bị bỏ: INVALID về nội dung; mindmap cũng thiếu nhóm collaboration-based (§4.5). (c) "Test monitoring & control" đánh số như bước thứ 2 của chuỗi tuần tự, trong khi §1.4.1 (tr. 18) nêu các hoạt động thường được thực hiện lặp hoặc song song: lỗi biểu diễn. Ba lỗi phụ: "Pesticide paradox" nay là "Tests wear out" (§1.3), "Technical Test Analyst" thuộc chương trình Advanced (§1.4.5), QC "detective" khác thuật ngữ "corrective" (§1.2.2). Kiểm chứng độc lập bằng Codex (Mục 17, 08:16 30/09/2026) cho kết quả khớp. |
| (5) Bản SV sửa | Mindmap đã sửa ở mục 4 của [qa-qc-roles.md](../req1-jobs/mindmap/qa-qc-roles.md): 5 test level, bỏ use case, thêm nhóm collaboration-based, đưa monitoring & control ra thành hoạt động chạy song song, đổi tên nguyên tắc 5. `[SV XÁC NHẬN]` đã tự mở giáo trình đối chiếu từng mục. |

### Artifact #2 — 5 lỗi AI/LLM (ChatGPT)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | ChatGPT Web — GPT 5.6 · 00:08 30/09/2026 · Prompt (đã ghi trong prompt log Mục 12): "Find 20 software defects publicized between 2022 and 2026. Mandatory: ≥ 5 defects related to AI/LLM (hallucination, prompt injection, bias). Each defect: source link, description, severity, consequences, solution." với yêu cầu này có nên bật web search trên chatgpt". `[TỰ ĐIỀN]` các prompt khác trong cuộc trò chuyện nếu có. |
| (2) Output AI | Nguyên văn câu trả lời gốc của ChatGPT do sinh viên dán trong prompt lúc 07:32:52 30/09/2026: [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). |
| (3) Verdict | INCOMPLETE |
| (4) Lý do | Case 4 (Air Canada) bị gắn nhãn "Hallucination" ở tiêu đề, bảng tóm tắt và mục Type, nhưng chính phần thân thừa nhận hồ sơ vụ án không nêu công nghệ chatbot; đây là gắn nhãn quá mức và tự mâu thuẫn (chi tiết ở Artifact #4). Case 3 (EmailGPT) chỉ nêu điểm của đơn vị cấp CVE (v4 8.5, v3.1 6.5) và bỏ điểm chính của NVD là 9.1 Critical (tra NVD API ngày 30/09/2026). Điểm CVSS của case 1 (9.8, NVD) và case 2 (8.1 v3.1, đơn vị cấp CVE) khớp nguồn; điểm CVSS v4 9.2 của case 2 chưa được đối chiếu. |
| (5) Bản SV sửa | Case 4 giữ trong danh sách nhưng đổi nhãn thành "incorrect generated response / hallucination-like failure"; case 3 nêu cả ba điểm và nguồn; case 1 dùng điểm NVD (9.8 v3.1); thay link bản án CanLII. Xem [defects.md](../req2-defects/defects.md). |

### Artifact #3 — 15 lỗi phần mềm còn lại (ChatGPT)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | ChatGPT Web — GPT 5.6 · 07:08 30/09/2026 · Prompt (prompt log Mục 13): "Hãy làm tương tự cho 15 software defects khác các sự cố/lỗ hõng này không nhất thiết phải liên quan đến AI/LLM mà có thể là lỗi phần mềm thông thường …" (nguyên văn đầy đủ ở prompt log). |
| (2) Output AI | Bản gốc của ChatGPT: `[TỰ ĐIỀN]` (chưa có trong repo; dán bản gốc hoặc link chia sẻ). Bản đang dùng: các case 6–20 trong [defects.md](../req2-defects/defects.md). |
| (3) Verdict | INCOMPLETE |
| (4) Lý do | Đối chiếu 14 CVE của các case 6–19 với NVD API: điểm nêu trong bài đúng theo nguồn (Spring4Shell 9.8, libwebp 8.8, glibc 7.8, OpenSSH 8.1, PHP-CGI 9.8, PAN-OS 10.0...). Thiếu điểm số ở case 7, 8, 9, 17 (chỉ ghi chữ). Case 12 (GitLab) và 13 (Confluence) ghi 10.0 của hãng, còn điểm chính của NVD là 9.8: cả hai đều có nguồn nhưng cần ghi rõ. Case 20 (CrowdStrike) không có CVE nên không có CVSS, đã ghi đúng. Chưa kiểm chứng từng câu mô tả kỹ thuật; 39/48 link mở được tự động, 8 link bị chặn công cụ tự động (sinh viên mở được), 1 link không kết nối được. |
| (5) Bản SV sửa | Bổ sung điểm 7.8, 9.8, 9.8, 8.6 cho case 7, 8, 9, 17; ghi cả điểm hãng và điểm NVD cho case 12, 13. `[SV XÁC NHẬN]` đã đọc lại mô tả kỹ thuật các case. |

### Artifact #4 — Mục "chỗ AI thiên lệch" (Phần C của defects.md)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 07:32:52 và 07:53:22 30/09/2026 · Prompt: "tôi đã dùng chatgpt bản web ... Và tôi tìm được một chỗ AI có vẻ đã bias, đó là ở case 4 ..." và "cứ giữ case 4 và thêm mục AI thiên lệch ..." |
| (2) Output AI | Phần C của [defects.md](../req2-defects/defects.md); lời phân tích ở [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md) (mốc 07:32:52 và 07:53:22). |
| (3) Verdict | VALID |
| (4) Lý do | Các trích dẫn nguyên văn của ChatGPT (tiêu đề, bảng, mục Type và câu "would be technically incorrect to claim ...") đều có trong câu trả lời gốc do sinh viên dán. Phát hiện do sinh viên nêu, AI chỉ viết lại. Phần giải thích nguyên nhân ("chiều theo khung của prompt") được ghi rõ là suy luận, không phải sự thật đã chứng minh. |
| (5) Bản SV sửa | `[SV XÁC NHẬN]` ghi các chỉnh sửa (nếu có) của sinh viên vào Phần C. |

### Artifact #5 — Mô tả công việc và kỹ năng yêu cầu của 10 tin tuyển dụng

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 (WebFetch không đăng nhập) · 22:42:31, 22:58:30 và 23:02:41 29/09/2026 · Prompt: "về các chỗ chưa đạt yêu cầu: ... mô tả công việc và kỹ năng bạn có thể extract từ nội dung các page đó ko? ...", "Phần kỹ năng của các job ko phải các thẻ ...", "hãy làm vậy và nhớ ghi prompt_log ..." |
| (2) Output AI | Nội dung mô tả và kỹ năng trong [jobs.md](../req1-jobs/jobs.md) (phiên bản đầu do AI viết); lời giải thích của AI ở các mốc trên trong [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). Kết quả WebFetch thô không có trong transcript. |
| (3) Verdict | INCOMPLETE |
| (4) Lý do | AI trích khi chưa đăng nhập nên thiếu và có chỗ mâu thuẫn: tin 2 chỉ trích được phần giới thiệu công ty, không có danh sách nhiệm vụ; lương tin 1 và 6 lấy từ phần phúc lợi khác với tiêu đề trong ảnh chụp (13–25 triệu so với 500–1,200 USD; "up to 35M" so với 800–1,500 USD); dòng yêu cầu AI của tin 6 được trích hai lần với hai cách diễn đạt khác nhau. Đây là kết quả đối chiếu với trang tin gốc và ảnh chụp của sinh viên, không có mục ISTQB tương ứng. |
| (5) Bản SV sửa | Sinh viên chép nguyên văn phần mô tả của tin 2, chốt lương theo tiêu đề trong ảnh chụp và đơn vị hiển thị, bỏ phần kỹ năng theo thẻ. `[SV XÁC NHẬN]` đã đối chiếu nguyên văn dòng AI của tin 6 trên trang thật. |

### Artifact #6 — AI Impact Analysis của 10 tin

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 23:08:32 29/09/2026 · Prompt: "giúp tôi điền AI Impact Analysis dựa trên các yêu cầu trong được ghi trong công việc và tình hình thực tế, ngắn gọn thôi" |
| (2) Output AI | 10 đoạn AI Impact Analysis (1–2 câu/tin) trong [jobs.md](../req1-jobs/jobs.md); nguyên văn phản hồi ở mốc 23:08:32 trong [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). |
| (3) Verdict | INCOMPLETE (tạm; sinh viên quyết định verdict cuối) |
| (4) Lý do | Nội dung bám vào mô tả và yêu cầu của từng tin, nhưng các nhận định về "tình hình thực tế" (mức độ AI thay thế từng vai trò, ví dụ tin 7 "ít bị thay thế nhất") là suy luận chung, không có nguồn. Không có mục ISTQB tương ứng với loại nhận định này. |
| (5) Bản SV sửa | `[TỰ ĐIỀN]` các đoạn sinh viên đã sửa hoặc viết lại. |

### Artifact #7 — 15 test case cho quạt Kenfan B4

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 09:13:39 30/09/2026 · Prompt: "Theo đề bài thì có vẻ nên là bạn tự tạo test case, sau đó tôi sẽ kiểm tra lại và thêm edge case, video tôi sẽ thêm sau khi có test cases. thiết bị và ảnh thiết bị tôi đã thêm vào sẵn" |
| (2) Output AI | Bản gốc, không sửa: [ai_testcases_original.md](ai_testcases_original.md) (15 test case, ba nhóm chức năng, các giả định về thiết bị). |
| (3) Verdict | INCOMPLETE |
| (4) Lý do | Đối chiếu với ISTQB CTFL v4.0.1: các test case chủ yếu là kịch bản thao tác, chưa áp dụng rõ kỹ thuật ở §4.2 (equivalence partitioning, boundary value analysis) hay state transition cho bộ nút bấm cơ; theo §1.4.1 test analysis phải xác định đủ tính năng cần test, nhưng AI bỏ hoàn toàn chức năng đảo gió vì không suy ra được từ ảnh. AI cũng tự đặt ngưỡng (3 giây, 30 phút, 10°) không có tài liệu nhà sản xuất. Test Case Checklist (Artifact #8) cho thấy 8 test case có expected chủ quan, 11 test case không có bước dọn dẹp, 02-001 vượt 20 phút. Ba chỗ AI bỏ sót được sinh viên tìm ra: nhấn đồng thời hai nút, chọn tốc độ khi không có điện rồi cấp điện, ngừng đảo gió. |
| (5) Bản SV sửa | Sinh viên thay 01-005, 02-005 và thay 03-005 bằng 04-001 (chức năng 04, đảo gió), đánh dấu `Y` ở cột "Edge case AI bỏ sót"; đã chạy 5 test case có video, kết quả 4 Pass và 1 Fail (01-005: hai nút cùng lún xuống). Xem [testcases.md](../req3-device/testcases.md). |

### Artifact #8 — Điền sheet Test Case Checklist

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 10:41:25 30/09/2026 · Prompt: "trước tiên hãy điền sheet checklist" |
| (2) Output AI | Sheet Sheet1 và "TC mapping" trong [HW01_TestcaseChecklist.xlsx](../req3-device/excel/HW01_TestcaseChecklist.xlsx); bảng kết quả trong [testcases.md](../req3-device/testcases.md); lời giải thích ở mốc 10:41:25 trong [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). |
| (3) Verdict | VALID (tạm; chờ sinh viên rà soát) |
| (4) Lý do | 27 tiêu chí lấy từ template Test Case Checklist; dấu `o/x/i` được điền theo nội dung từng test case (ví dụ 11 test case không có bước tắt quạt bị đánh `x` ở tiêu chí self-cleaning). Đánh giá chủ quan của AI, không có mục ISTQB tương ứng ngoài tinh thần §1.4.1 về test design/implementation. |
| (5) Bản SV sửa | `[TỰ ĐIỀN]` các dấu sinh viên đổi sau khi rà soát. |

### Artifact #9 — Bản nháp mô tả bug 01-005 (đã gỡ bỏ)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 10:34:52 30/09/2026 · Prompt: "tôi đã thêm video và actual ouput của các test trong video" (AI tự ghi thêm bug từ test case 01-005 fail). |
| (2) Output AI | Trong sheet Bug report của `HW01_TestSummaryReport.xlsx` và `bugs/README.md`, AI viết: tóm tắt "Hai nút tốc độ 1 và 2 cùng lún xuống khi nhấn đồng thời (không có cơ cấu khóa liên động)" cùng ba bước tái hiện. Nội dung này đã bị xóa khỏi file; nguyên văn ghi lại ở đây và ở lời giải thích của AI tại mốc 10:34:52 trong [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). |
| (3) Verdict | INVALID (loại bỏ) |
| (4) Lý do | Thoả thuận AI mục 11 quy định bug report do 100% sinh viên viết, AI không được nháp mô tả. Việc AI viết mô tả là vi phạm quy định, không phải lỗi kỹ thuật của nội dung. |
| (5) Bản SV sửa | Đã thay bằng `[SV TỰ VIẾT]` ở lượt làm việc lúc 11:01:41 30/09/2026 (prompt log Mục 25); `[SV XÁC NHẬN]` sinh viên tự viết mô tả bug từ quan sát của mình. |

### Artifact #10 — Bản nháp AI Critique (200–300 từ)

| Mục | Nội dung |
|---|---|
| (1) Prompt + công cụ | Claude Code — Sonnet 5.5 · 11:04:20 30/09/2026 · Prompt: "Tiếp tục với AI-05 và Ai critique" |
| (2) Output AI | Đoạn 278 từ ở mục 5 của [report/HW01_report.md](../report/HW01_report.md); nguyên văn phản hồi ở mốc 11:04:20 30/09/2026 trong [transcripts/2026-09-29_30_session_main.md](transcripts/2026-09-29_30_session_main.md). |
| (3) Verdict | INCOMPLETE (tạm; sinh viên viết lại) |
| (4) Lý do | Các dữ kiện trong đoạn (lỗi mindmap, nhãn hallucination của case Air Canada, điểm NVD 9.1 của EmailGPT, chức năng đảo gió và test case 01-005, việc AI tự viết mô tả bug) đều truy được về Artifact #1, #2, #7, #9 và đã được kiểm chứng. Tuy nhiên AI Critique là phản tư của chính sinh viên; phần giải thích nguyên nhân ("chiều theo khung câu hỏi") là suy luận, không phải sự thật đã chứng minh. |
| (5) Bản SV sửa | `[TỰ ĐIỀN]` sinh viên viết lại bằng lời của mình, giữ trong 200–300 từ. |

## 4. Tổng kết độ chính xác AI

| Chỉ số | Số lượng | Tỉ lệ |
|---|---|---|
| Tổng artifact AI sinh đã audit | 10 | 100% |
| VALID (đúng, dùng nguyên) | 2 | 20% |
| INVALID (sai; loại bỏ) | 1 | 10% |
| INCOMPLETE (chấp nhận sau khi sửa) | 7 | 70% |

Ghi chú: verdict của Artifact #6, #8 và #10 là tạm thời; Artifact #9 bị loại vì vi phạm quy định về bug report, không phải vì lỗi kỹ thuật. Trong các artifact INCOMPLETE có những thành phần sai nội dung ở mức chi tiết (mindmap: test level, use case testing; ChatGPT: nhãn hallucination cho case 4), nhưng toàn artifact vẫn được giữ sau khi sửa.

## 5. Kết luận — Khi nào nên / không nên dùng AI?

AI mạnh ở việc dựng khung, tổng hợp nhanh và sinh test case phổ thông. Nó sai khi dùng kiến thức bản cũ (mindmap ghi CTFL 4.0 nhưng dùng nội dung bản 2018), gắn nhãn theo khung của người hỏi (case Air Canada) và bỏ sót tình huống chỉ thấy khi thao tác trên thiết bị thật (nhấn hai nút cùng lúc, chức năng đảo gió). Trích dẫn số liệu cũng không nhất quán giữa các lần hỏi. Nên dùng AI để lập bản nháp và khung, sau đó kiểm chứng từng khẳng định bằng nguồn gốc như giáo trình ISTQB và NVD. Không nên dùng AI để thiết kế edge case, thực thi test trên thiết bị hoặc tạo bằng chứng.

## 6. Mandatory Disclosure

> Bản nháp, sinh viên xác nhận và chỉnh lại trước khi nộp.

"Báo cáo, danh sách lỗi phần mềm, mindmap, test case và checklist này được sinh phiên bản đầu bởi Claude (Claude Code, Sonnet 5.5) và ChatGPT (GPT 5.6); tôi đã rà soát và chỉnh sửa `[SV XÁC NHẬN: các phần đã sửa]`, bổ sung các edge case 01-005, 02-005 và 04-001; ảnh thiết bị cùng thẻ sinh viên, video thực thi, kết quả thực tế của test case, ảnh chụp tin tuyển dụng và `[SV XÁC NHẬN: các phần khác]` do tôi tự thực hiện. AI Audit Report chi tiết đính kèm ở Phụ lục A. Tôi cam đoan không dùng AI để sinh bất kỳ artifact nào thuộc danh mục bị cấm."

## Chữ ký

| Mục | Giá trị |
|---|---|
| Họ tên sinh viên (in hoa) | NGUYỄN PHÚ DINH |
| MSSV | 23120031 |
| Lớp / Khoá | `[TỰ ĐIỀN]` |
| Môn học | CS423 / CSC13003 – Kiểm chứng Phần mềm |
| Giảng viên | TS. Lâm Quang Vũ / TS. Trần Duy Hoàng / ThS. Trần Thị Bích Hạnh / ThS. Trương Phước Lộc / ThS. Hồ Tuấn Thanh |
| Ngày | `[TỰ ĐIỀN]` |
| Chữ ký | `[SV KÝ]` |

## Tham khảo
- ISTQB Certified Tester Foundation Level Syllabus v4.0.1 (15/09/2024): https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf
- NVD (National Vulnerability Database) REST API, truy cập 30/09/2026.
- Kharbach, M. (2026). AI Use Policy Templates for Higher Education. CC BY-NC-SA 4.0.
