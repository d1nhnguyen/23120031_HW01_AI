# Phụ lục A — Prompt log

Mỗi mục gồm: timestamp `HH:MM dd/mm/yyyy`, công cụ, prompt đầy đủ, phản hồi đầy đủ (hoặc link ảnh chụp).

Công cụ chung: Claude Code (VSCode extension), model Claude Sonnet 5.5.

> Ghi chú cho sinh viên: timestamp của Mục 01–03 là ước lượng (≈) dựa trên thời điểm tạo file; phản hồi của Mục 01–03 chưa được chép nguyên văn — cần dán lại từ transcript Claude Code trước khi nộp.

## Mục 01

- Timestamp: ≈ 21:50 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "Đọc các yêu cầu trong @Homeworks/ và @Templates/ để gợi ý cấu trúc thư mục nộp bài phù hợp"
- Phản hồi: đề xuất cây thư mục nộp bài (report/, req1-jobs/, req2-defects/, req3-device/, ai/, git-log.txt) kèm các lưu ý về tên zip, template Excel, AI-02/03/05, mâu thuẫn điểm R3 (40 vs 25).
  <!-- TODO: dán nguyên văn từ transcript -->
- Ảnh hưởng đến bài nộp: chỉ là cấu trúc thư mục, không phải nội dung bài làm.

## Mục 02

- Timestamp: ≈ 22:12 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "Có, hãy tạo giúp tôi"
- Phản hồi: tạo khung thư mục, các file `.md` mẫu, copy 3 template Excel, `git init`.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 03

- Timestamp: ≈ 22:16 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "tôi nghĩ nên dùng tiếng việt cho hw01 này"
- Phản hồi: dịch các file `.md` mẫu sang tiếng Việt, giữ tên mục bắt buộc bằng tiếng Anh trong ngoặc.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 04 — Kiểm tra 10 tin tuyển dụng (Yêu cầu 1)

- Timestamp: 22:30 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (đọc 10 ảnh chụp bằng Read; đọc 10 link bằng WebFetch, không đăng nhập)
- Prompt: "nhớ điền prompt log khi cần thiết, hiện tại tôi đã thêm vào screenshots của 10 job tôi tìm được trên hai trang itviec và linkedin, tôi đã đánh dấu 3 jobs mà trong description có yêu cầu ai, verify lại giúp tôi. nếu có sai sót so với yêu cầu thì hãy chỉ rõ. trong @software_testing/hw01/job.md có chứa 10 link của các job theo thứ tự, hãy tìm hiểu và báo lại với tôi"
- Phản hồi (dữ liệu AI thu thập từ link, chưa được sinh viên kiểm chứng lại trên trình duyệt):

| #   | Công ty / vị trí                                | Đăng    | Lương (ảnh chụp)      | Lương (WebFetch)                     | Nội dung AI trong JD (WebFetch)                                                                            | Mức yêu cầu AI           |
| --- | ----------------------------------------------- | ------- | --------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------- | ------------------------ |
| 1   | QIG — Manual Tester                             | 6 ngày  | 500–1,200 USD         | (không đăng nhập: không thấy)        | "ứng dụng công nghệ mới và AI vào công việc hàng ngày" (dòng văn hoá)                                      | Không                    |
| 2   | Saritasa — QA Engineer                          | 6 ngày  | 1,000–1,500 USD       | $1,000–1,500                         | Thẻ kỹ năng "AI"; "Comfortable using AI tools to speed up test design" (Preferred)                         | Điểm cộng                |
| 3   | GoldenGate — Junior/Middle QA                   | 8 ngày  | ẩn ("You'll love it") | —                                    | Không                                                                                                      | Không                    |
| 4   | MiTek — Manual/Automation Tester                | 14 ngày | ẩn                    | —                                    | Không                                                                                                      | Không                    |
| 5   | Saigon Technology — Middle/Senior Automation QC | 5 ngày  | ẩn                    | —                                    | "Experience in using AI in automating test scripts / test cases" (nice-to-have)                            | Điểm cộng                |
| 6   | TrustedAI — Automation Tester (JP N3+)          | 6 ngày  | 800–1,500 USD         | "Up to 35M VND" (mâu thuẫn ảnh chụp) | "ứng dụng AI vào các tác vụ test"; "test sản phẩm AI/chatbot hoặc NLP là điểm cộng"                        | Có (đánh dấu ✔)          |
| 7   | ECARX — PQA                                     | 10 ngày | ẩn                    | —                                    | Không                                                                                                      | Không                    |
| 8   | OL Vietnam — QA Engineer                        | 32 ngày | ẩn                    | —                                    | Không (chỉ automation nice-to-have)                                                                        | Không                    |
| 9   | SCC — AI QA Engineer (LinkedIn)                 | 3 tuần  | không có              | Không nêu                            | Test "Scout" AI agent trên MS Teams; yêu cầu kinh nghiệm test giao diện hội thoại / ứng dụng AI, EU AI Act | Có (đánh dấu ✔)          |
| 10  | Ins Enco — Senior QA (AI-Augmented) (LinkedIn)  | 1 tuần  | không thấy            | 30–40 triệu VND gross                | "Use GPT / Claude to generate test cases…", Postbot, Mabl/Testim, Applitools/Percy                         | Có, rõ nhất (đánh dấu ✔) |

Kết luận của AI: 3 tin đã đánh dấu (6, 9, 10) đều có nội dung AI trong JD → đạt ≥ 3. Sai sót so với đề: (a) ảnh chụp chỉ có ngày tương đối ("6 ngày trước"), không có ngày tuyệt đối; (b) 7/10 tin không hiện mức lương (3, 4, 5, 7, 8, 9 và 10 nếu không cuộn tới phần JD); (c) ảnh job6/9/10 không hiện dòng JD chứng minh yêu cầu AI; (d) thiếu JD/kỹ năng nằm ngoài khung ảnh (phải ghi vào jobs.md); (e) mọi tin nằm trong 60 ngày (tin cũ nhất OL Vietnam ≈ 28/08/2026).

- Cách sinh viên xử lý sau đó: ghi ngày chụp 29/09/2026 vào jobs.md (trang không hiện ngày cụ thể); chấp nhận ghi "Không công bố" cho tin không có lương; nộp ngày 30/09/2026 nên hạn 60 ngày không phải vấn đề.

## Mục 05 — Điền jobs.md từ nội dung các tin (Yêu cầu 1)

- Timestamp: 22:44 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (WebFetch 10 link không đăng nhập, sau đó Claude dịch/tóm tắt sang tiếng Việt)
- Prompt: "về các chỗ chưa đạt yêu cầu:

1. Hiện tại tạm thời sẽ thêm ngày chụp trong jobs.md, do trên các trang này ko hiện ngày cụ thể.
2. tôi nghĩ theo hướng "Không công bố" vẫn ổn, hoặc nếu có thể bạn hãy tìm giúp tôi các jobs khác để thay vào.
3. yêu cầu ai sẽ có trong phần description
4. mô tả công việc và kỹ năng bạn có thể extract từ nội dung các page đó ko? nếu ko hãy label các chỗ đó để tôi tự điền vào.
5. tôi nộp ngay vào ngày mai nên ko phải vấn đề."

- Phản hồi: Claude điền `req1-jobs/jobs.md` (bảng tổng hợp + mô tả/yêu cầu/kỹ năng từng tin) — nội dung đầy đủ nằm trong file đó. Phần Claude không trích được hoặc do sinh viên phải viết được gắn nhãn `[TỰ ĐIỀN]` / `[TỰ KIỂM TRA]` (AI Impact Analysis, mô tả công việc tin 02, kiểm chứng lương tin 01/06/07/10, ảnh chụp bổ sung).
  <!-- TODO: dán nguyên văn kết quả WebFetch và phản hồi từ transcript khi lập AI Audit Report -->
- Lưu ý kiểm chứng: hai lần WebFetch cho tin 06 diễn đạt dòng yêu cầu AI khác nhau ("ứng dụng AI vào các tác vụ test" và "Automation testing and AI application experience") — cần đối chiếu nguyên văn trên trang. Đây là chỗ AI có thể diễn giải sai/không nhất quán, có thể dùng cho phần AI Critique.

## Mục 06 — Bỏ kỹ năng theo thẻ, chỉ giữ mô tả công việc và kỹ năng yêu cầu

- Timestamp: ≈ 22:55 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "Phần kỹ năng của các job ko phải các thẻ trên itviec hay linkedin mà nằm trong yêu cầu công việc. chỉ cần 2 mục: job description và required skills (mô tả công việc và kỹ năng yêu cầu) bỏ phần kỹ năng như này đi: "- Kỹ năng (thẻ ITviec): Tester, Mobile Apps, QA QC.""
- Phản hồi: Claude sửa `req1-jobs/jobs.md`: xoá các dòng kỹ năng theo thẻ, dòng địa điểm và dòng "Yêu cầu AI" riêng; mỗi tin còn "Mô tả công việc" và "Kỹ năng yêu cầu" (lấy từ mục Yêu cầu của trang); viết lại cột kỹ năng trong bảng tổng hợp.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 07 — Hỏi về sự phù hợp của các field với yêu cầu đề

- Timestamp: ≈ 23:00 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "đây là yêu cầu: "Each posting: link, dated screenshot, job description, required skills, salary.", các fields để như hiện tại có hợp lý chưa?"
- Phản hồi: Claude đối chiếu các field hiện tại với yêu cầu và đề xuất: ghi ngày chụp theo từng tin, gom đủ các field vào mỗi tin, nhúng ảnh vào Markdown để PDF hiển thị ảnh, làm gọn bảng tổng hợp và bỏ cột kỹ năng trùng lặp.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 08 — Áp dụng cấu trúc mới cho jobs.md và ghi prompt log

- Timestamp: 23:05 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "hãy làm vậy và nhớ ghi prompt_log tất cả những gì tôi và bạn làm việc"
- Phản hồi: Claude viết lại `req1-jobs/jobs.md`: bảng tổng hợp còn 5 cột (#, Công ty/Vị trí, Ngày chụp, Lương, Yêu cầu AI?); mỗi tin có một khối gồm link, ngày chụp và ngày đăng ước tính, ảnh nhúng, lương, mô tả công việc, kỹ năng yêu cầu, yêu cầu AI, AI Impact Analysis. Bản sao lưu trước khi sửa nằm ở thư mục scratchpad của phiên làm việc. Claude ghi thêm Mục 06–08 vào file này.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 09 — "continue"

- Timestamp: 23:05 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "continue"
- Phản hồi: Claude kiểm tra lại `jobs.md` (10 khối tin, mỗi khối đủ trường) rồi ghi các mục prompt log trên.

## Mục 10 — Soạn AI Impact Analysis cho 10 tin

- Timestamp: 23:08 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "giúp tôi điền AI Impact Analysis dựa trên các yêu cầu trong được ghi trong công việc và tình hình thực tế, ngắn gọn thôi"
- Phản hồi: Claude soạn 10 đoạn AI Impact Analysis (1–2 câu/tin) và ghi vào `req1-jobs/jobs.md`; nội dung nằm trong file đó. Đây là artifact do AI tạo → cần một mục trong AI-02 Audit Report (verdict VALID/INVALID/INCOMPLETE + sinh viên sửa lại).
  <!-- TODO: dán nguyên văn từ transcript -->
- Lưu ý: nhận định về "tình hình thực tế" (mức độ AI thay thế từng công việc) là suy luận chung của AI, không kèm nguồn; sinh viên cần kiểm chứng/chỉnh sửa và có thể dùng làm chỗ phản biện AI.

## Mục 11 — Chốt lương, ảnh chụp và dọn ghi chú jobs.md

- Timestamp: ≈ 23:15 29/09/2026
- Công cụ: Claude Code — Sonnet 5.5
- Prompt: "các mức lương chốt như hiện tại là ổn, chỉ có khác biệt đơn vị tính, và vị trí nêu mức lương, tin 2 tôi đã thêm nguyên văn thông tin trong mô tả công việc của họ. ảnh tin 6 9 10 như hiện tại tôi nghĩ đã ổn rồi, thấy được đầy đủ ngày đăng và profile của tôi"
- Phản hồi: Claude xoá các ghi chú `[TỰ KIỂM TRA]` (lương, ảnh bổ sung) khỏi `req1-jobs/jobs.md`, thêm dòng giải thích đơn vị/vị trí lương ở đầu file, và đồng bộ lương tin 7 giữa bảng tổng hợp và khối chi tiết theo giá trị sinh viên đã chọn trong bảng.
  <!-- TODO: dán nguyên văn từ transcript -->
- Quyết định của sinh viên: giữ lương như hiện tại (đơn vị USD/VND tuỳ trang); ảnh tin 6, 9, 10 giữ nguyên, không chụp thêm; mô tả công việc tin 02 do sinh viên tự chép nguyên văn.

## Mục 12 — Kiểm tra defects.md (Yêu cầu 2) và phân tích chỗ AI thiên lệch ở case 4

- Timestamp: 07:44 30/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (đọc file, gọi NVD REST API để đối chiếu CVSS của 17 CVE, kiểm tra HTTP status 48 link)
- Prompt: "tôi đã dùng chatgpt bản web với web search để tổng hợp thông tin cho @23120031_HW01_AI/req2-defects/defects.md , hãy kiểm tra xem đúng cấu trúc và yêu cầu của đề bài chưa? Và tôi tìm được một chỗ AI có vẻ đã bias, đó là ở case 4. Đây là nguyên văn câu trả lời ban đầu của AI: "<nguyên văn câu trả lời ChatGPT về 5 defect AI, sinh viên dán vào — xem transcript>" trong câu trả lời gốc này AI xếp case 4 vào llm hallucination dù chưa khẳng định được."
- Phản hồi: Claude đối chiếu defects.md với yêu cầu R2 (20 lỗi, ≥ 5 lỗi AI, mỗi lỗi có link/mô tả/severity/hậu quả/giải pháp, 1 chỗ AI thiên lệch hoặc hallucinate), báo thiếu mục "AI thiên lệch", đối chiếu điểm CVSS với NVD và kiểm tra link.
  <!-- TODO: dán nguyên văn từ transcript -->
- Việc sinh viên phải bổ sung cho ChatGPT (công cụ AI đã dùng để tạo defects.md): prompt gốc + timestamp + toàn bộ output (mỗi lần hỏi một mục), và một mục trong AI-02 Audit Report cho defects.md.

## Mục 15 — Sửa defects.md: thêm mục AI thiên lệch, chỉnh CVSS, link Air Canada

- Timestamp: 07:54 30/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (NVD API để tra CVE-2025-32711; sửa file)
- Prompt: "cứ giữ case 4 và thêm mục AI thiên lệch, phần link tôi vẫn mở được bình thường. các phần còn lại hãy làm như bạn đã nhận xét"
- Phản hồi: Claude sửa `req2-defects/defects.md`: thêm Phần C (chỗ AI thiên lệch ở case 4, kèm quan sát bổ sung ở case 3); thay link Air Canada bằng bản án CanLII; chỉnh điểm CVSS theo NVD (case 1, 3, 7, 8, 9, 12, 13, 17 và bảng tổng hợp); thêm phụ lục case AI dự phòng (EchoLeak, CVE-2025-32711) ngoài 20 case. Bản sao lưu trước khi sửa nằm ở thư mục scratchpad.
  <!-- TODO: dán nguyên văn từ transcript -->
- Lưu ý: phần Phần C và phụ lục do AI soạn; sinh viên cần rà soát, đặc biệt các mục `[TỰ KIỂM TRA]` ở phụ lục và giải thích nguyên nhân thiên lệch (là suy luận, không được chứng minh).

## Mục 13 — Tìm 5 Software Defects có liên quan AI/

- Timestamp: 00:08 30/09/2026
- Công cụ: ChatGPT Web - GPT 5.6
- Prompt: ""Find 20 software defects publicized between 2022 and 2026.
  Mandatory: ≥ 5 defects related to AI/LLM (hallucination, prompt injection, bias).
  Each defect: source link, description, severity, consequences, solution."  với yêu cầu này có nên bật web search trên chatgpt"
- Phản hồi: ChatGPT trả về 5 Software Defects có liên quan đến AI/LLM.

## Mục 14 — Tìm 15 Software Defects

- Timestamp: 07:08 30/09/2026
- Công cụ: ChatGPT Web - GPT 5.6
- Prompt: "Hãy làm tương tự cho 15 software defects khác các sự cố/lỗ hõng này không nhất thiết phải liên quan đến AI/LLM mà có thể là lỗi phần mềm thông thường, vẫn nêu đầy đủ defect name, source link, description, severity, consequences, solution như trên, sau khi thực hiện xong tổng hợp 2 kết quả tìm kiếm lại thành một file markdown tiếng việt."
- Phản hồi: ChatGPT trả về file markdown tiếng Việt có đầy đủ 20 Software Defects.

## Mục 16 — Tạo mindmap QA/QC (G9.1) và tìm 3 lỗi
- Timestamp: 08:10 30/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (tải giáo trình ISTQB CTFL v4.0.1 từ istqb.org để đối chiếu, vẽ ảnh bằng Python/Pillow)
- Prompt: "tôi đã xóa phần phụ lục, mục req2 xem như đã xong, giờ hãy tạo mindmap QA/QC"
- Phản hồi: Claude tạo `req1-jobs/mindmap/qa-qc-roles.png` (bản gốc), `qa-qc-roles_annotated.png` (đánh dấu lỗi) và `qa-qc-roles.md` (mã Mermaid, 3 lỗi chính, 3 lỗi phụ, bản sửa); cập nhật `README.md` cùng thư mục.
  <!-- TODO: dán nguyên văn từ transcript -->
- Lưu ý: mindmap và audit do cùng một AI thực hiện; các lỗi đã đối chiếu với file PDF chính thức nhưng sinh viên phải tự xác nhận trên giáo trình và viết lại phần Reasoning bằng lời của mình. Đây là artifact do AI tạo → cần một mục AI-02.

## Mục 17 — Đối chiếu độc lập 3 lỗi trong mindmap với giáo trình ISTQB chính thức

- Timestamp: 08:16 30/09/2026
- Công cụ: Codex — GPT-5 (đọc các file trong `req1-jobs/mindmap/` và tra cứu website ISTQB chính thức)
- Prompt: "So sánh với giáo trình ISTQB chính thức tìm thử 3 lỗi trong @23120031_HW01_AI/req1-jobs/mindmap/ , không được bịa ra, mỗi lỗi phải có trích dẫn và link rõ ràng để tôi có thể đối chiếu. ghi [prompt_log.md](23120031_HW01_AI/ai/prompt_log.md)"
- Phản hồi đầy đủ:

  Nguồn chuẩn dùng để đối chiếu là **ISTQB Certified Tester Foundation Level Syllabus v4.0.1**, ngày 15/09/2024, lấy từ trang ISTQB chính thức: [trang chứng chỉ CTFL v4.0](https://www.istqb.org/certifications/certified-tester-foundation-level-ctfl-v4-0/) và [PDF syllabus chính thức](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf).

  | # | Nội dung trong mindmap | Kết quả đối chiếu và trích dẫn | Kết luận |
  |---|---|---|---|
  | 1 | Nhánh **Test Levels** chỉ ghi `Component → Integration → System → Acceptance`, tức bốn mức và gộp chung Integration. | CTFL v4.0.1 §2.2.1 ghi “**following five test levels**”, rồi liệt kê riêng: Component, **Component integration**, System, **System integration**, Acceptance. Xem [PDF chính thức, §2.2.1, tr. 28–29](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf#page=29). Phụ lục thay đổi cũng xác nhận integration đã được tách thành hai mức; xem [tr. 75](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf#page=75). | **INVALID:** mindmap thiếu một test level và dùng cách gộp Integration không đúng với CTFL 4.0.1. |
  | 2 | Nhánh **Black-box** có `Use case`. | CTFL v4.0.1 §4.2 chỉ liệt kê bốn kỹ thuật black-box: equivalence partitioning, boundary value analysis, decision table testing và state transition testing; xem [PDF chính thức, §4.2, tr. 39](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf#page=39). Phụ lục thay đổi nói rõ “**Use case testing removed**”; xem [tr. 75](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf#page=75). | **INVALID:** `Use case testing` không còn thuộc nội dung CTFL v4.0.1. |
  | 3 | Nhánh **ISTQB Test Process** đánh số `1…7`, trong đó `Test monitoring & control` là bước số 2; cách vẽ dễ được hiểu là một chuỗi bước tuần tự. | CTFL v4.0.1 §1.4.1 nói các hoạt động kiểm thử thường được thực hiện “**iteratively or in parallel**”; đồng thời test monitoring là việc kiểm tra liên tục các hoạt động kiểm thử. Xem [PDF chính thức, §1.4.1, tr. 18–19](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf#page=18). | **INCOMPLETE/MISLEADING:** tên bảy nhóm hoạt động không sai, nhưng cách đánh số không thể hiện tính lặp/song song và tính liên tục của monitoring. Đây là lỗi biểu diễn, không phải khẳng định rằng `Test monitoring & control` không thuộc test process. |

  Kết luận kiểm chứng: cả ba điểm đều có căn cứ trực tiếp trong syllabus chính thức. Tuy nhiên phải phân loại đúng: lỗi 1 và 2 là sai nội dung; lỗi 3 là thiếu ngữ cảnh do cách trực quan hóa. Không dùng nhận định “AI trộn bản cũ” như một sự thật vì syllabus chỉ chứng minh nội dung khác nhau, không chứng minh được nguyên nhân nội bộ khiến AI trả lời sai.

## Mục 18 — Cập nhật mindmap sau khi có kết quả kiểm chứng độc lập
- Timestamp: 08:20 30/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (kiểm tra link PDF bằng curl, sửa `req1-jobs/mindmap/qa-qc-roles.md`)
- Prompt: "Tôi đã nhờ codex verify lại và đã đọc source và xác minh được 3 lỗi trong @23120031_HW01_AI/ai/prompt_log.md"
- Phản hồi: Claude đọc Mục 17 và thấy 3 lỗi chính khớp với kết quả của Claude ở Mục 16. Claude sửa `qa-qc-roles.md`: bỏ nhận định về nguyên nhân AI sai (không được chứng minh), đổi verdict lỗi 3 thành INCOMPLETE/MISLEADING, dẫn link PDF chính thức và ghi việc đã được kiểm chứng độc lập ở Mục 17.
  <!-- TODO: dán nguyên văn từ transcript -->

## Mục 19 — Tạo khung Yêu cầu 3 (thiết bị vật lý) theo đề và template
- Timestamp: 08:28 30/09/2026
- Công cụ: Claude Code — Sonnet 5.5 (đọc cấu trúc 3 file Excel template, dựng khung bằng openpyxl, kiểm tra hiển thị bằng LibreOffice)
- Prompt: "đối với yêu cầu 3 tạo sẵn khung đáp ứng yêu cầu bài tập và đúng templates tôi sẽ tự điền vào thiết bị và các test cases, sau đó tôi sẽ yêu cầu verify lại"
- Phản hồi: Claude tạo khung trong `req3-device/`: `device.md`, `testcases.md`, `videos.md`, `bugs/README.md`; dựng lại 3 file Excel từ template (`HW01_TestCases.xlsx`, `HW01_TestcaseChecklist.xlsx`, `HW01_TestSummaryReport.xlsx`) và cập nhật mục 3 trong `report/HW01_report.md`. Bản sao lưu 3 file Excel trước khi sửa nằm ở thư mục scratchpad.
  <!-- TODO: dán nguyên văn từ transcript -->

## Việc còn lại cho sinh viên trước khi nộp

- Dán nguyên văn phản hồi của Claude vào các mục có `TODO` (Mục 01–03, 05–08, 10–12, 15–16, 18–19) từ transcript Claude Code; timestamp có dấu ≈ là ước lượng.
- Rà soát/chỉnh sửa AI Impact Analysis do AI soạn (Mục 10) và điền mô tả công việc tin 02.
- Đối chiếu nguyên văn dòng yêu cầu AI của tin 6 trên trang thật (hai lần trích của AI khác nhau).
- Điền mục "Cách sinh viên xử lý sau đó" cho các mục còn thiếu, tạo bản PDF cho jobs.md.
- Điền Yêu cầu 3 (device.md, testcases.md, Excel, videos.md) rồi yêu cầu verify; chỉ ghi vào prompt log các lần dùng AI để tạo test case cùng prompt, timestamp và output đầy đủ.
