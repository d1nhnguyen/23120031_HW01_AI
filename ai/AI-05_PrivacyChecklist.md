# [AI-05] Bảng kiểm Quyền riêng tư & Sử dụng AI có trách nhiệm — HW01-AI

Khoa Công nghệ Thông tin (FIT) – Trường Đại học Khoa học Tự nhiên (HCMUS) · CS423 / CSC13003 – Kiểm chứng Phần mềm (AI-augmented · 2026)

> **Trạng thái:** bản nháp do AI soạn. Chỉ sinh viên mới xác nhận được các khẳng định về bản thân, nên cột "Sinh viên tick" chỉ được tick sẵn khi có bằng chứng rõ trong bài. Sinh viên phải đọc lại, sửa dấu tick cho đúng sự thật rồi ký.

## 1. Trước khi dùng AI

| Mục | Sinh viên tick | Bằng chứng / ghi chú |
|---|---|---|
| Đã xác nhận Cấp độ AI cho bài tập này | [x] | AI-03 ghi Cấp 4 theo thoả thuận mục 4 (HW#01–HW#06). `[SV XÁC NHẬN]` |
| Dùng tài khoản Claude Pro tự chọn (không phải tài khoản cá nhân) | [ ] | `[SV XÁC NHẬN]` Câu chữ của mẫu chưa rõ; đề HW01 nói khoa không cấp tài khoản trả phí, sinh viên tự chọn công cụ. Nêu rõ công cụ và loại tài khoản đã dùng. |
| Đã đọc Thoả thuận AI của môn học | [ ] | `[SV XÁC NHẬN]` Biểu mẫu AI-06 phải được ký từ tuần 1. |
| Hiểu rõ artifact nào KHÔNG được sinh bằng AI | [ ] | `[SV XÁC NHẬN]` Lưu ý: AI từng tự nháp mô tả bug (đã gỡ, xem AI-03 và AI-02 Artifact #9). |

## 2. Trong khi dùng AI

| Mục | Sinh viên tick | Bằng chứng / ghi chú |
|---|---|---|
| Không nhập dữ liệu cá nhân của bạn, khách hàng, bệnh nhân | [ ] | **Không đạt hoàn toàn** — xem "Ngoại lệ cần khai báo" bên dưới. |
| Không paste nguyên si tài liệu có bản quyền lên AI | [ ] | `[SV XÁC NHẬN]` AI đọc file đề HW01 và các biểu mẫu do giảng viên cung cấp, và tải giáo trình ISTQB CTFL v4.0.1 (tài liệu công khai trên istqb.org) để tra cứu từng mục; không có đoạn nào được dán nguyên si. |
| Không paste code công ty / code open-source giới hạn license | [x] | Không có code nào được đưa lên AI. Các script Python do AI viết chỉ để dựng ảnh và file Excel. |
| Đã ghi mọi prompt + phản hồi AI vào prompt_log.md có timestamp | [ ] | Chưa đủ: các prompt ChatGPT ở Mục 12 còn thiếu và Mục 13 chưa có output gốc. Các mục Claude Code đã có giờ chính xác và nguyên văn trong `transcripts/`. |

## 3. Trước khi nộp bài

| Mục | Sinh viên tick | Bằng chứng / ghi chú |
|---|---|---|
| Mọi artifact AI sinh đã được gắn tag trong AI Audit Report | [x] | [AI-02_AuditReport.md](AI-02_AuditReport.md) có 10 artifact. Artifact #3 còn thiếu output gốc của ChatGPT. |
| Mọi trích dẫn AI đã được xác minh (nguồn thực sự tồn tại) | [ ] | Điểm CVSS của 17 CVE đã đối chiếu NVD; link trong `defects.md` (48 link) sinh viên xác nhận mở được. Mô tả kỹ thuật từng lỗi chưa kiểm chứng hết. `[SV XÁC NHẬN]` |
| Mọi code AI sinh đã được thực thi và test | [x] | Các script dựng ảnh mindmap và Excel đã chạy và được kiểm tra bằng cách xuất ảnh/PDF; không có code nào nằm trong bài nộp. |
| AI Critique 200–300 chữ đã có trong báo cáo | [ ] | Bản nháp đã có ở mục 5 của [report/HW01_report.md](../report/HW01_report.md); sinh viên viết lại rồi mới tick. |
| Đoạn Mandatory Disclosure ở cuối báo cáo | [ ] | Mới có bản nháp trong AI-02 mục 6; báo cáo chính chưa hoàn thành. |
| Đính kèm AI Use Disclosure Form | [ ] | [AI-03_Disclosure.md](AI-03_Disclosure.md) đã soạn nhưng chưa ký. |
| Sẵn sàng cho vấn đáp ngẫu nhiên 5–7 phút tuần kế nộp bài | [ ] | `[SV XÁC NHẬN]` Chuẩn bị: chạy lại một test case trên thiết bị, giải thích vì sao chọn input đó, chỉ ra một lỗi AI mắc mà bạn đã sửa (ví dụ mindmap hoặc case Air Canada). |

## Ngoại lệ cần khai báo — dữ liệu cá nhân

- Ảnh thiết bị kèm thẻ sinh viên (`req3-device/device_with_student_id.jpg`, có họ tên, ngày sinh, MSSV) đã được AI (Claude) đọc lúc 09:14:00 30/09/2026 để xác định thiết bị. Ảnh chụp màn hình tin tuyển dụng (hiện tên tài khoản và địa chỉ email) cũng được AI đọc lúc 22:29:30 29/09/2026 khi kiểm tra Yêu cầu 1.
- Vì vậy mục "Không nhập dữ liệu cá nhân của bạn" không tick. Đây là việc đã xảy ra, không hoàn tác được; nêu rõ để trợ giảng biết. `[SV XÁC NHẬN]` cách xử lý (ví dụ: từ nay che ngày sinh và email trước khi cho AI đọc).
- Bản nộp cuối có thể che các thông tin không bắt buộc (ngày sinh trên thẻ, email) nếu đề cho phép.

## 4. Cam đoan cuối cùng

Trách nhiệm cuối cùng về độ chính xác, tính nguyên bản, và liêm chính của bài nộp này thuộc về tôi. Mọi việc dùng AI không khai báo đều bị coi là vi phạm liêm chính học thuật.

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
