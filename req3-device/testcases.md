# Yêu cầu 3 — 15 Test Case cho thiết bị

Nguồn dữ liệu gốc là [excel/HW01_TestCases.xlsx](excel/HW01_TestCases.xlsx). Bảng dưới đây là bản sao để đưa vào báo cáo (chính sách: bảng tổng hợp từ Excel phải được copy vào file Markdown).

## Yêu cầu của đề

- Thiết kế **15 test case**, mỗi test case có: Objective / Input / Steps / Expected / Actual / Verdict.
- **≥ 3 test case là edge case mà công cụ AI KHÔNG tìm ra.**
- Thực thi **≥ 5 test case trên thiết bị thật** và quay video ≤ 60 giây (có giọng nói của bạn), đăng YouTube Unlisted, ghi link ở [videos.md](videos.md).
- Test case do AI tạo phải có mục trong AI Audit Report ([AI-02]): prompt, output, verdict, reasoning, bản sửa.

## Ánh xạ cột đề bài sang cột trong template Excel

| Cột theo đề             | Cột trong `HW01_TestCases.xlsx` (sheet Test cases) |
| ----------------------- | -------------------------------------------------- |
| Objective               | Test case name                                     |
| Input + Steps           | Test step (ghi rõ giá trị input trong từng bước)   |
| Expected                | Expected Result                                    |
| Actual                  | Actual Result                                      |
| Verdict                 | Status (Pass / Fail / Untested)                    |
| ≥ 3 edge case AI bỏ sót | Cột thêm K: Edge case AI bỏ sót? (Y/N)             |
| ≥ 5 video               | Cột thêm L: Video                                  |

Quy ước ID: `NN - 00M` (NN là số chức năng, M là số thứ tự test case), theo mẫu của template.

## Danh sách chức năng (khớp sheet Function list)

| ID  | Chức năng                                 | Mô tả                                                                            |
| --- | ----------------------------------------- | -------------------------------------------------------------------------------- |
| 01  | Điều khiển bằng nút bấm (bật/tắt, tốc độ) | Các nút bấm ở đế quạt: tắt và các mức tốc độ (giả định 3 mức).                   |
| 02  | Vận hành và hiệu năng cơ bản              | Chạy liên tục, độ ổn định, độ ồn, lưu lượng và hướng gió, chạy lại sau mất điện. |
| 03  | An toàn và độ chắc chắn cơ khí            | Lồng bảo vệ, dây điện/phích cắm, cánh quạt, góc nghiêng, mặt đặt nghiêng.        |

## Bảng 15 test case

| ID     | Objective                                                                 | Input                                                                       | Steps                                                                                                                                                        | Expected                                                                                                                                    | Actual | Verdict  | Edge case AI bỏ sót? | Đã thực thi + video? | Ghi chú                                                                                           |
| ------ | ------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- | -------------------- | -------------------- | ------------------------------------------------------------------------------------------------- |
| 01-001 | Bật quạt ở tốc độ 1 bằng nút bấm                                          | Nhấn nút tốc độ 1.                                                          | 1. Nhấn nút tốc độ 1<br>2. Quan sát cánh quạt và cảm nhận gió phía trước<br>3. Ghi lại thời gian từ lúc nhấn đến lúc cánh quay đều                           | 1. Cánh quạt quay và có gió ra phía trước<br>2. Quạt khởi động trong khoảng 3 giây<br>3. Không có tiếng lạ hoặc mùi khét                    |        | Untested | N                    |                      | Điều kiện: Quạt đặt trên mặt phẳng, phích cắm vào ổ 220V, quạt đang tắt (nút Off đang được nhấn). |
| 01-002 | Chuyển tốc độ tăng dần 1 → 2 → 3                                          | Nhấn lần lượt nút tốc độ 2 rồi nút tốc độ 3, chờ 5 giây sau mỗi lần nhấn.   | 1. Nhấn nút tốc độ 2, chờ 5 giây, quan sát<br>2. Nhấn nút tốc độ 3, chờ 5 giây, quan sát                                                                     | 1. Tốc độ quay và lưu lượng gió tăng rõ sau mỗi lần nhấn<br>2. Quạt không tắt giữa các lần chuyển                                           |        | Untested | N                    |                      | Điều kiện: Quạt đang chạy ở tốc độ 1.                                                             |
| 01-003 | Chuyển tốc độ giảm dần 3 → 2 → 1                                          | Nhấn lần lượt nút tốc độ 2 rồi nút tốc độ 1, chờ 5 giây sau mỗi lần nhấn.   | 1. Nhấn nút tốc độ 2, chờ 5 giây, quan sát<br>2. Nhấn nút tốc độ 1, chờ 5 giây, quan sát                                                                     | 1. Tốc độ quay và lưu lượng gió giảm rõ sau mỗi lần nhấn<br>2. Quạt không tắt giữa các lần chuyển                                           |        | Untested | N                    |                      | Điều kiện: Quạt đang chạy ở tốc độ 3.                                                             |
| 01-004 | Tắt quạt bằng nút Off khi đang chạy tốc độ 3                              | Nhấn nút Off.                                                               | 1. Nhấn nút Off<br>2. Quan sát cánh quạt cho đến khi dừng hẳn<br>3. Ghi lại thời gian cánh dừng                                                              | 1. Cánh quạt giảm tốc và dừng hẳn<br>2. Nút Off giữ nguyên vị trí đã nhấn<br>3. Không có tiếng va chạm hoặc tiếng lạ khi dừng               |        | Untested | N                    |                      | Điều kiện: Quạt đã chạy ở tốc độ 3 ít nhất 1 phút.                                                |
| 01-005 | Nhấn đổi nút liên tục và nhanh                                            | Nhấn xen kẽ các nút 1, 2, 3, Off khoảng 20 lần trong 10 giây.               | 1. Nhấn liên tục các nút theo thứ tự 1, 2, 3, Off, lặp lại khoảng 20 lần trong 10 giây<br>2. Dừng ở nút tốc độ 2 và quan sát quạt 10 giây                    | 1. Nút không bị kẹt hoặc không nhả<br>2. Quạt chạy đúng theo nút được nhấn cuối cùng<br>3. Không có tia lửa, mùi khét; cầu dao không nhảy   |        | Untested | N                    |                      | Điều kiện: Quạt cắm điện, đang tắt.                                                               |
| 02-001 | Chạy liên tục 30 phút ở tốc độ 3 (nhiệt độ và độ bền)                     | Chạy tốc độ 3 liên tục 30 phút.                                             | 1. Bật tốc độ 3<br>2. Mỗi 10 phút, đặt mu bàn tay lên thân động cơ phía sau 1–2 giây<br>3. Ghi nhận tốc độ quay, tiếng ồn và mùi tại mỗi mốc 10, 20, 30 phút | 1. Thân động cơ ấm nhưng không nóng đến mức không thể chạm<br>2. Không có mùi khét<br>3. Tốc độ quay và tiếng ồn ổn định, quạt không tự tắt |        | Untested | N                    |                      | Điều kiện: Quạt đặt nơi thoáng, phòng có nhiệt độ bình thường, quạt đang tắt.                     |
| 02-002 | Độ ổn định của đế khi chạy tốc độ 3                                       | Chạy tốc độ 3 trong 5 phút.                                                 | 1. Bật tốc độ 3<br>2. Quan sát độ rung và vị trí đế quạt trong 5 phút                                                                                        | 1. Quạt không xê dịch trên mặt bàn<br>2. Không rung lắc mạnh, không đổ                                                                      |        | Untested | N                    |                      | Điều kiện: Quạt đặt trên mặt bàn phẳng, khô.                                                      |
| 02-003 | Độ ồn theo từng mức tốc độ                                                | Tốc độ 1, 2, 3; mỗi mức chạy 1 phút, đo ở khoảng cách 1 m.                  | 1. Bật tốc độ 1, đo và ghi độ ồn (dB) hoặc nghe bằng tai<br>2. Lặp lại với tốc độ 2 và tốc độ 3                                                              | 1. Độ ồn tăng dần theo tốc độ<br>2. Không có tiếng rít, cọ xát hoặc gõ lạch cạch ở cả 3 mức                                                 |        | Untested | N                    |                      | Điều kiện: Phòng yên tĩnh, ứng dụng đo độ ồn trên điện thoại (nếu có), quạt đang tắt.             |
| 02-004 | Lưu lượng và hướng gió theo tốc độ                                        | Tốc độ 1, 2, 3; mỗi mức chạy 30 giây.                                       | 1. Bật tốc độ 1, quan sát dải ruy băng<br>2. Lặp lại với tốc độ 2 và tốc độ 3                                                                                | 1. Dải ruy băng bay về phía trước quạt<br>2. Mức độ bay tăng dần theo tốc độ                                                                |        | Untested | N                    |                      | Điều kiện: Dải ruy băng hoặc giấy mỏng treo trước quạt, cách 0,5 m, ngang tầm cánh quạt.          |
| 02-005 | Chạy lại sau khi mất điện đột ngột                                        | Rút phích cắm, chờ 10 giây, cắm lại (nút vẫn ở tốc độ 2).                   | 1. Rút phích cắm khi quạt đang chạy tốc độ 2<br>2. Chờ 10 giây<br>3. Cắm phích lại vào ổ điện, không thao tác nút                                            | 1. Quạt tự chạy lại ở tốc độ 2<br>2. Không có tia lửa ở phích cắm hoặc ổ điện                                                               |        | Untested | N                    |                      | Điều kiện: Quạt đang chạy ở tốc độ 2.                                                             |
| 03-001 | Lồng bảo vệ chắc chắn và khe hở an toàn                                   | Lắc nhẹ lồng bằng tay; thử đưa một ngón tay qua khe lưới về phía cánh quạt. | 1. Lắc nhẹ lồng trước bằng tay<br>2. Kiểm tra các kẹp cố định lồng<br>3. Thử đưa một ngón tay qua khe lưới về phía cánh quạt                                 | 1. Lồng không lỏng lẻo, các kẹp giữ chắc<br>2. Ngón tay không chạm được vào cánh quạt qua khe lưới                                          |        | Untested | N                    |                      | Điều kiện: Rút phích cắm, quạt tắt.                                                               |
| 03-002 | Điều chỉnh góc nghiêng đầu quạt (chỉ thực hiện nếu quạt có chỉnh nghiêng) | Nghiêng đầu quạt lên xuống ở vài góc khác nhau.                             | 1. Nới núm hoặc khớp nghiêng<br>2. Nghiêng đầu quạt lên và xuống ở vài góc<br>3. Siết lại, cắm điện và chạy tốc độ 3 trong 1 phút                            | 1. Đầu quạt giữ đúng góc đã chọn khi chạy<br>2. Không tự sụp hoặc trượt, khớp không kêu                                                     |        | Untested | N                    |                      | Điều kiện: Rút phích cắm, quạt tắt.                                                               |
| 03-003 | Kiểm tra dây điện và phích cắm                                            | Quan sát và kiểm tra bằng tay vỏ dây, chỗ nối dây, chân phích.              | 1. Kiểm tra toàn bộ vỏ dây điện<br>2. Kiểm tra chỗ dây nối vào thân quạt<br>3. Kiểm tra chân phích cắm                                                       | 1. Vỏ dây không nứt, không hở lõi, không cháy xém<br>2. Chỗ nối chắc, không lỏng<br>3. Chân phích không cong, không gỉ hoặc đổi màu         |        | Untested | N                    |                      | Điều kiện: Rút phích cắm, quạt tắt.                                                               |
| 03-004 | Cánh quạt cân bằng và không chạm lồng                                     | Quay cánh bằng tay vài vòng; sau đó chạy tốc độ 3.                          | 1. Dùng tay quay cánh quạt vài vòng<br>2. Quan sát khe hở giữa cánh và lồng<br>3. Cắm điện, chạy tốc độ 3 và quan sát cánh khi quay                          | 1. Cánh quay trơn và không chạm lồng<br>2. Cánh không lắc hoặc nghiêng khi chạy<br>3. Cánh không nứt, mẻ                                    |        | Untested | N                    |                      | Điều kiện: Rút phích cắm, quạt tắt.                                                               |
| 03-005 | Vận hành trên mặt nghiêng nhẹ (khoảng 10°)                                | Chạy tốc độ 1 rồi tốc độ 3, mỗi mức 1 phút.                                 | 1. Đặt quạt lên mặt nghiêng<br>2. Bật tốc độ 1 trong 1 phút, quan sát<br>3. Chuyển sang tốc độ 3 trong 1 phút, quan sát                                      | 1. Quạt không tự trượt và không đổ<br>2. Không có tiếng lạ                                                                                  |        | Untested | N                    |                      | Điều kiện: Tấm ván nghiêng khoảng 10° đặt ổn định; quạt đặt xa mép; tay sẵn sàng rút phích.       |

## Phân tích test case do AI tạo (G9.3 — Analyse)

Mục tiêu: chứng minh bạn tìm được **≥ 3 edge case mà AI bỏ sót** khi kiểm thử thiết bị thật.

### Prompt và test case AI đã tạo

- Công cụ / prompt / timestamp: xem [ai/prompt_log.md](../ai/prompt_log.md) Mục `[TỰ ĐIỀN]`
- Danh sách test case AI đề xuất: `[TỰ ĐIỀN]`

### Edge case AI bỏ sót (≥ 3)

| #   | Test case (ID) | Edge case   | Vì sao AI bỏ sót | Kết quả trên thiết bị thật |
| --- | -------------- | ----------- | ---------------- | -------------------------- |
| 1   | `[TỰ ĐIỀN]`    | `[TỰ ĐIỀN]` | `[TỰ ĐIỀN]`      | `[TỰ ĐIỀN]`                |
| 2   | `[TỰ ĐIỀN]`    | `[TỰ ĐIỀN]` | `[TỰ ĐIỀN]`      | `[TỰ ĐIỀN]`                |
| 3   | `[TỰ ĐIỀN]`    | `[TỰ ĐIỀN]` | `[TỰ ĐIỀN]`      | `[TỰ ĐIỀN]`                |

## Tổng kết thực thi

Copy từ sheet Test summary report của [excel/HW01_TestSummaryReport.xlsx](excel/HW01_TestSummaryReport.xlsx):

| No  | Function ID | Function name                             | Pass | Fail | Untested | Number of test cases |
| --- | ----------- | ----------------------------------------- | ---- | ---- | -------- | -------------------- |
| 1   | 01          | Điều khiển bằng nút bấm (bật/tắt, tốc độ) | 0    | 0    | 5        | 5                    |
| 2   | 02          | Vận hành và hiệu năng cơ bản              | 0    | 0    | 5        | 5                    |
| 3   | 03          | An toàn và độ chắc chắn cơ khí            | 0    | 0    | 5        | 5                    |
|     |             | Total                                     | 0    | 0    | 15       | 15                   |

## Danh sách kiểm tra

- [ ] Đủ 15 test case, mỗi test case đủ Objective / Input / Steps / Expected / Actual / Verdict
- [ ] ≥ 3 edge case AI bỏ sót, đã đánh dấu Y ở cột K
- [ ] ≥ 5 test case đã thực thi trên thiết bị thật, có video tương ứng
- [ ] Đã điền [excel/HW01_TestcaseChecklist.xlsx](excel/HW01_TestcaseChecklist.xlsx) cho TC1–TC15
- [ ] Sheet Test summary report khớp với sheet Test cases
- [ ] Bảng tổng hợp trên khớp với Excel
- [ ] Mỗi test case do AI tạo có mục trong AI-02
