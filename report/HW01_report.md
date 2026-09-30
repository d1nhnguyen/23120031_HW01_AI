# Báo cáo HW01-AI

## 1. Yêu cầu 1 — Thị trường việc làm QA/QC 2026+
<!-- Copy bảng tổng hợp từ req1-jobs/jobs.md -->

## 2. Yêu cầu 2 — 20 lỗi phần mềm 2022–2026
<!-- Copy bảng tổng hợp từ req2-defects/defects.md -->

## 3. Yêu cầu 3 — Test case cho sản phẩm vật lý
### 3.1 Thiết bị
<!-- Copy từ req3-device/device.md: brand, model, năm, serial đã che, ảnh thiết bị + thẻ sinh viên -->

### 3.2 15 test case
<!-- Copy bảng từ req3-device/testcases.md; đánh dấu ≥ 3 edge case AI bỏ sót -->

### 3.3 Thực thi và video
<!-- Copy bảng link YouTube Unlisted (≥ 5) từ req3-device/videos.md -->

### 3.4 Tổng kết và bug
<!-- Copy Test Summary Report từ req3-device/excel/HW01_TestSummaryReport.xlsx; bug (nếu có) xem req3-device/bugs/ -->

## 4. AI Audit Report (Báo cáo kiểm toán AI)
<!-- Tóm tắt; chi tiết từng artifact nằm trong ai/AI-02_AuditReport.pdf.
     Nêu tỉ lệ VALID / INVALID / INCOMPLETE và KHI NÀO nên / không nên dùng AI cho công việc này -->

## 5. AI Critique (Phản biện AI, 200–300 từ)

<!-- Bản nháp do AI (Claude) soạn từ các bằng chứng đã kiểm chứng; sinh viên viết lại bằng lời của mình và giữ trong 200–300 từ (bản nháp: 278 từ). -->

Trong HW01, AI giúp dựng bản nháp nhanh nhưng sai ở những chỗ cần nguồn gốc hoặc vật thật. Thứ nhất, mindmap ISTQB do AI vẽ ghi nhãn CTFL 4.0 nhưng chỉ có 4 test level, xếp use case testing vào black-box và đánh số "test monitoring & control" như một bước tuần tự. Đối chiếu giáo trình v4.0.1 cho thấy có 5 mức, use case testing đã bị bỏ, và các hoạt động thường chạy lặp hoặc song song. Thứ hai, ChatGPT gắn nhãn hallucination cho vụ Air Canada dù chính câu trả lời thừa nhận hồ sơ không nêu công nghệ chatbot; tôi cho rằng AI cần một ví dụ cho nhóm tôi yêu cầu nên gắn nhãn quá mức (đây là suy luận của tôi). Nó cũng bỏ sót điểm 9.1 của NVD ở lỗ hổng EmailGPT. Thứ ba, khi sinh test case cho quạt, AI bỏ sót chức năng đảo gió vì không thấy trong ảnh, và bỏ sót việc nhấn đồng thời hai nút, đúng tình huống làm test case 01-005 thất bại trên thiết bị thật. AI còn tự viết mô tả bug dù quy định cấm, vì nó không tự nhớ ràng buộc của môn học. Nguyên nhân chung là AI dựa vào kiến thức phổ biến hoặc cũ, tự tin quá mức, chiều theo khung câu hỏi và không có vật thật để thử. Nguyên tắc tôi rút ra: coi đầu ra AI là giả thuyết cần kiểm chứng bằng nguồn gốc (giáo trình, NVD, thiết bị thật), yêu cầu AI tách sự kiện có nguồn khỏi suy luận, và tự thiết kế edge case từ tương tác vật lý.

## 6. Mandatory Disclosure (Khai báo bắt buộc)
> "[Test case / script / dataset / báo cáo] ban đầu được tạo bởi [tên công cụ AI]; tôi đã rà soát và chỉnh sửa [phần X], bổ sung [edge case Y, Z]; [phần W] do tôi tự viết hoàn toàn. AI Audit Report chi tiết được đính kèm ở Phụ lục A. Tôi xác nhận không dùng AI để tạo bất kỳ artifact nào thuộc nhóm bị cấm nêu dưới đây."

## 7. Tự đánh giá (Self-Assessment)

| STT | Tiêu chí | Điểm | Tự chấm |
|---|---|---|---|
| 1 | Thị trường việc làm 2026+ (10 tin × 3 điểm + AI Impact) | 40 | |
| 2 | Lỗi phần mềm 2022–2026 (20 lỗi) | 20 | |
| 3 | Thiết kế test cho sản phẩm vật lý (15 TC + 5 video) | 25 | |
| AI-1 | Đính kèm [AI-02] AI Audit Report (5 phần) | 8 | |
| AI-2 | AI Critique 200–300 từ + đính kèm [AI-03] Disclosure | 4 | |
| AI-3 | [AI-05] Checklist đã ký + bằng chứng chống gian lận | 3 | |
| | Tổng | 100 | |

## Phụ lục A — Prompt log
Xem [ai/prompt_log.md](../ai/prompt_log.md).
