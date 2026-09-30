# Phiên Claude Code 29/09/2026 — lên kế hoạch HW01 và dọn thư mục Templates

Công cụ: Claude Code (VSCode extension), model Claude Sonnet 5.5. Xuất tự động từ file transcript của Claude Code: chỉ gồm lời nhắn của sinh viên và câu trả lời bằng chữ của AI; không gồm nội dung gọi công cụ (đọc/ghi file, lệnh shell). Giờ theo múi giờ máy (UTC+7). Phiên chính vẫn đang diễn ra nên cần xuất lại trước khi nộp.


---

### [21:57:40 29/09/2026] SINH VIÊN

Đọc và tìm hiểu kỹ các yêu cầu trong hw và lên plan thực hiện hw01, như gợi ý cấu trúc thư mục như thế nào, nộp những thứ gì,...


---

### [21:57:43 29/09/2026] AI (Claude)

Tôi sẽ xem thư mục để tìm các file yêu cầu của HW01.


---

### [21:58:15 29/09/2026] AI (Claude)

Tôi xem thêm các template AI bắt buộc để lên plan cho đúng.


---

### [21:58:51 29/09/2026] AI (Claude)

# Kế hoạch HW01-AI

Tôi đã đọc `___2026.Homework.Policies.md`, file HW01 và các template AI-02, 03, 05, 06. Tôi chưa tạo file nào.

## 1. Những điểm cần lưu ý

- **Điểm.** Bảng rubric cho R3 là 25 điểm, còn mô tả yêu cầu ghi 40. Rubric cộng lại đúng 100 nên tôi lấy rubric làm chuẩn: R1 40, R2 20, R3 25, AI-1 8, AI-2 4, AI-3 3.
- **Định dạng.** Viết bằng Markdown và xuất thêm bản PDF. Excel dùng được, nhưng bảng tổng hợp phải copy vào file Markdown.
- **Git.** Mỗi bước trong mỗi requirement là một commit có message rõ ràng, và phải nộp git log.
- **Link ngoài.** Chính sách nói lạm dụng link online sẽ bị 0 điểm. Vì vậy ảnh, screenshot và file phải nằm trong zip. Chỉ video để link YouTube Unlisted, và đề bài cũng cho phép link GitHub.
- **Mâu thuẫn trong đề.** Ba chỗ đề nói không khớp nhau:
  - Phần nộp bài yêu cầu "Bug screenshots: FIT Mantis", nhưng HW01 không có yêu cầu tìm bug trên Mantis.
  - Mindmap ISTQB/QA-QC (G9.1, tìm 3 lỗi của AI) không được liệt kê thành yêu cầu riêng, nhưng lại có trong danh sách nộp.
  - AI-05 ghi "tài khoản Claude Pro".
  
  Nên hỏi TA qua Moodle forum, hoặc làm dư cho chắc: chụp trang chủ Mantis có username là MSSV, và làm mindmap.
- **Chống gian lận.** Bốn thứ không được dùng AI sinh, vi phạm là 0 điểm và bị chuyển kỷ luật:
  1. Ảnh thiết bị cùng thẻ SV trong một khung hình.
  2. Video thực thi có giọng của chính bạn.
  3. 10 screenshot job có hiện tên tài khoản.
  4. Prompt log có timestamp.
- **Quyền riêng tư.** Không đưa thẻ SV hay số serial thật vào AI. Che 4 ký tự giữa của serial trước khi ghi vào báo cáo.
- **Vấn đáp.** 30% sinh viên bị gọi ngẫu nhiên. Cần chạy lại được một test case, giải thích vì sao chọn input đó, và chỉ ra một lỗi AI mắc mà bạn đã sửa. Trượt từ 2 câu thì điểm nhân 0.5.

## 2. Cấu trúc thư mục đề xuất

Đây cũng là cấu trúc của repo Git.

```
StudentID_HW01_AI/
├── README.md                      # mục lục, cách đọc bài
├── report/
│   ├── HW01_Report.md             # báo cáo chính
│   └── HW01_Report.pdf            # bản Save-as-PDF
│   #   Nội dung: R1, R2, R3, AI Audit Report, AI Critique,
│   #   Mandatory Disclosure (đặt trước phụ lục), Self-assessment
├── appendix/
│   ├── A_prompt_log.md            # mọi prompt + timestamp HH:MM dd/mm/yyyy
│   ├── AI-02_AuditReport.md/.pdf  # 5 mục cho mỗi artifact
│   ├── AI-03_DisclosureForm.pdf   # ký
│   └── AI-05_PrivacyChecklist.pdf # ký
├── r1_jobs/
│   ├── jobs.md                    # 10 job: link, JD, skills, lương, AI Impact
│   ├── screenshots/job01..10.png  # có ngày và tên tài khoản
│   └── mindmap/qaqc_mindmap.md|png  # AI vẽ, bạn đánh dấu 3 lỗi
├── r2_defects/
│   └── defects.md                 # 20 defect, ≥5 liên quan AI/LLM
├── r3_physical/
│   ├── device_id_photo.jpg        # thiết bị + thẻ SV cùng khung hình
│   ├── device_info.md             # brand, model, năm, serial (che 4 ký tự giữa)
│   ├── testcases.xlsx             # 15 TC (dùng Test Case Template) + summary
│   ├── testcases.md               # bảng TC copy vào Markdown
│   ├── ai_missed_edgecases.md     # ≥3 edge case AI không tìm ra
│   └── videos.md                  # ≥5 link YouTube Unlisted, tiêu đề map với TC ID
├── mantis/                        # nếu TA xác nhận cần: ảnh trang chủ Mantis
└── git_log.txt                    # xuất từ git log --oneline --stat
```

Tên zip: `StudentID_HW01_AI_<grade>.zip`, ví dụ `21120000_HW01_AI_085.zip`. Grade gồm 3 chữ số. Mỗi file không quá 20MB, tối đa 20 file. Nếu vượt thì dùng split-and-zip.

## 3. Nội dung từng requirement

**R1 – Job market (40 điểm, khoảng 1h30)**
- Tìm 10 job QA/QC đăng trong vòng 60 ngày tính đến ngày nộp, trên LinkedIn, TopCV, ITviec, Indeed. Cần ít nhất 3 job yêu cầu AI/LLM/automation-AI.
- Mỗi job cần link, screenshot có ngày và tên tài khoản của bạn, mô tả công việc, kỹ năng, lương, và 1–2 câu AI Impact Analysis. Điểm là 3 điểm mỗi job, cộng thêm phần AI Impact.
- Nên chụp ngay khi tìm được, vì tin có thể bị gỡ.
- Mindmap: nhờ AI vẽ mindmap ISTQB/QA-QC, tìm 3 lỗi và ghi vào Audit Report.
- Tổng kết ngắn: việc nào AI thay thế được, hỗ trợ được, không thay thế được.

**R2 – 20 defects (20 điểm, khoảng 1h)**
- Chọn 20 lỗi phần mềm được công bố từ 2022 đến 2026, trong đó ≥5 lỗi liên quan AI/LLM (hallucination, prompt injection, bias). Nên đa dạng ngành: hàng không, tài chính, cloud outage, bảo mật.
- Mỗi lỗi ghi source link, mô tả, severity, hậu quả, giải pháp.
- Bắt buộc tìm 1 chỗ AI bị thiên lệch hoặc bịa khi giải thích defect. Cách làm: nhờ AI giải thích một số defect, rồi đối chiếu với nguồn gốc.
- Kiểm tra link có thật, vì AI hay bịa nguồn.

**R3 – Test thiết bị vật lý (25 điểm, khoảng 2h)**
- Chọn một thiết bị bạn có sẵn và dễ chứng minh hành vi bằng video, ví dụ quạt, nồi cơm điện, bóng đèn thông minh.
- Chụp ảnh thiết bị cùng thẻ SV trong một khung hình. Ghi brand, model, năm, serial đã che 4 ký tự giữa.
- Thiết kế 15 TC theo cột Objective / Input / Steps / Expected / Actual / Verdict.
- Quy trình: nhờ AI sinh TC trước, rồi tìm ≥3 edge case AI bỏ sót và ghi vào `ai_missed_edgecases.md`. Đây chính là mục G9.3.
- Chạy ≥5 TC trên máy thật, quay video ≤60 giây, nói bằng giọng của bạn, đăng YouTube Unlisted.
- Chọn thiết bị an toàn. Không thử các TC nguy hiểm như đổ nước vào thiết bị điện.

**Phần AI (15 điểm, làm song song với ba phần trên)**
- **AI-1 (8 điểm), Audit Report.** Mỗi artifact do AI sinh (mindmap, bộ TC, giải thích defect) có một hàng theo 5 mục: prompt + tool + timestamp, output nguyên văn, verdict VALID/INVALID/INCOMPLETE, lý do dẫn ISTQB/slide, bản bạn sửa. Cuối báo cáo tính tỉ lệ VALID/INVALID/INCOMPLETE và kết luận khi nào nên hoặc không nên dùng AI.
- **AI-2 (4 điểm).** Viết AI Critique 200–300 từ, và điền AI-03 Disclosure Form.
- **AI-3 (3 điểm).** Ký AI-05 và có đủ các bằng chứng chống gian lận.
- Đề nói thiếu Audit Report, prompt log hoặc critique thì mất cả cột AI Compliance, nên phải ghi prompt log ngay từ prompt đầu tiên.

## 4. Thứ tự làm và commit (tổng khoảng 5h)

| Bước | Việc | Commit (ví dụ) |
|---|---|---|
| 0 | Tạo repo, khung thư mục, `prompt_log.md`, ký AI-06 nếu chưa nộp | `chore: init repo structure and prompt log` |
| 1 | Chọn thiết bị, chụp ảnh với thẻ SV, ghi device info | `r3: add device photo and info` |
| 2 | R1: thu thập 10 job, chụp screenshot | `r1: add job postings 1-5`, `r1: add jobs 6-10 + AI impact` |
| 3 | R1: mindmap do AI vẽ, tìm 3 lỗi | `r1: add AI mindmap and 3 corrections` |
| 4 | R2: 20 defect, đối chiếu nguồn | `r2: add 20 defects`, `r2: add AI hallucination finding` |
| 5 | R3: AI sinh TC, tìm edge case AI bỏ sót, bổ sung TC | `r3: add AI-generated TCs`, `r3: add 3 missed edge cases` |
| 6 | R3: chạy 5 TC, quay và upload video, điền Actual/Verdict | `r3: execute TCs and add video links` |
| 7 | Audit Report, Critique, Disclosure, Self-assessment | `ai: add audit report`, `ai: add critique and disclosure` |
| 8 | Xuất PDF, ký AI-03 và AI-05, đóng zip, xuất git log | `release: final report and submission zip` |

## 5. Việc cần làm trước

1. Xác nhận ngày deadline trên Moodle. Job phải đăng trong 60 ngày trước ngày nộp.
2. Chọn thiết bị.
3. Hỏi TA hai điểm: Mantis có cần không, và mindmap được tính vào R1 hay là mục riêng.

Bạn muốn tôi tạo sẵn khung thư mục, file Markdown mẫu cho từng phần, `prompt_log.md` và `git init` không? Bạn cũng cho tôi biết đã chọn thiết bị nào. Tôi sẽ soạn bộ TC mẫu theo đúng thiết bị đó, nhưng phần edge case AI bỏ sót và các bằng chứng chống gian lận vẫn phải là của bạn.


---

### [22:01:27 29/09/2026] SINH VIÊN

vậy xóa bớt các thứ không cần thiết hiện tại trong @Templates/


---

### [22:01:43 29/09/2026] AI (Claude)

Zip gốc vẫn còn trong Downloads nên xóa xong vẫn khôi phục được. Tôi giữ các template dùng cho HW01 (test case, test report, bug list) và xóa phần còn lại.


---

### [22:02:06 29/09/2026] AI (Claude)

Tôi đã xóa 11 file lẻ và cả thư mục `UI Checklist/` (16 file) khỏi `Templates/`. Còn lại 6 file:

- `Test Cases/Test cases_Template_En.xlsx`
- `Test Cases/Testcase Checklist.xlsx`
- `Test Case Template.xls`
- `TRs and TCs Template.xls`
- `Test report_Template_En.xlsx`
- `Bug list.xls`

- **Giữ lại:** đề HW01 yêu cầu nộp Excel gồm Test Cases, Checklist và Test Summary Report, nên tôi giữ các template test case và test report. Bug list tôi giữ vì file nhỏ và có thể cần nếu TA yêu cầu Mantis.
- **Đã xóa:** các template test plan (IEEE, RUP, PDF, PPT), Usability, phiếu đánh giá Seminar, template thu thập yêu cầu (YCPM) và toàn bộ UI/GUI checklist. HW01 kiểm thử thiết bị vật lý nên không dùng đến chúng.
- **Khôi phục:** file gốc vẫn còn trong `Downloads/CSC13003-CQ-Software Testing-CT4-VN-20260929T145334Z-1-001.zip`. Các HW sau có thể cần lại test plan hoặc UI checklist, khi đó giải nén lại từ zip này.

Bạn có muốn tôi dựng khung thư mục HW01 theo kế hoạch trước không?
