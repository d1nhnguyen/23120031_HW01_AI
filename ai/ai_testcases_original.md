# Test case do AI tạo — bản gốc (không sửa)

- Công cụ: Claude Code — Sonnet 5.5
- Timestamp: 09:16 30/09/2026
- Prompt: "Theo đề bài thì có vẻ nên là bạn tự tạo test case, sau đó tôi sẽ kiểm tra lại và thêm edge case, video tôi sẽ thêm sau khi có test cases. thiết bị và ảnh thiết bị tôi đã thêm vào sẵn" (kèm ảnh `req3-device/device_with_student_id.jpg` và `device.md`)
- Thiết bị: quạt điện Kenfan B4 (theo `device.md`).
- Mục đích: lưu bản gốc để so sánh với danh sách cuối cùng, phục vụ phần G9.3 (tìm ≥ 3 edge case AI bỏ sót) và [AI-02] AI Audit Report. **Không sửa file này.**

## Giả định của AI về thiết bị (chưa được xác nhận)
- Ảnh cho thấy 4 nút bấm ở đế quạt (nút đầu màu tối, ba nút còn lại sáng); nhãn nút không đọc được. AI giả định: Off, tốc độ 1, tốc độ 2, tốc độ 3.
- Không biết quạt có quay/đảo chiều, hẹn giờ, điều khiển từ xa hay không: các test case không dùng các chức năng này.
- TC 03-002 (góc nghiêng) chỉ thực hiện nếu quạt có chỉnh nghiêng.
- Các ngưỡng như "3 giây", "30 phút", "10°" là giá trị hợp lý do AI chọn, không lấy từ tài liệu nhà sản xuất (không có datasheet).


## Function 01: Điều khiển bằng nút bấm (bật/tắt, tốc độ)

### 01-001 — Bật quạt ở tốc độ 1 bằng nút bấm
- **Precondition:** Quạt đặt trên mặt phẳng, phích cắm vào ổ 220V, quạt đang tắt (nút Off đang được nhấn).
- **Input:** Nhấn nút tốc độ 1.
- **Steps:**
  1. Nhấn nút tốc độ 1
  2. Quan sát cánh quạt và cảm nhận gió phía trước
  3. Ghi lại thời gian từ lúc nhấn đến lúc cánh quay đều
- **Expected:**
  1. Cánh quạt quay và có gió ra phía trước
  2. Quạt khởi động trong khoảng 3 giây
  3. Không có tiếng lạ hoặc mùi khét

### 01-002 — Chuyển tốc độ tăng dần 1 → 2 → 3
- **Precondition:** Quạt đang chạy ở tốc độ 1.
- **Input:** Nhấn lần lượt nút tốc độ 2 rồi nút tốc độ 3, chờ 5 giây sau mỗi lần nhấn.
- **Steps:**
  1. Nhấn nút tốc độ 2, chờ 5 giây, quan sát
  2. Nhấn nút tốc độ 3, chờ 5 giây, quan sát
- **Expected:**
  1. Tốc độ quay và lưu lượng gió tăng rõ sau mỗi lần nhấn
  2. Quạt không tắt giữa các lần chuyển

### 01-003 — Chuyển tốc độ giảm dần 3 → 2 → 1
- **Precondition:** Quạt đang chạy ở tốc độ 3.
- **Input:** Nhấn lần lượt nút tốc độ 2 rồi nút tốc độ 1, chờ 5 giây sau mỗi lần nhấn.
- **Steps:**
  1. Nhấn nút tốc độ 2, chờ 5 giây, quan sát
  2. Nhấn nút tốc độ 1, chờ 5 giây, quan sát
- **Expected:**
  1. Tốc độ quay và lưu lượng gió giảm rõ sau mỗi lần nhấn
  2. Quạt không tắt giữa các lần chuyển

### 01-004 — Tắt quạt bằng nút Off khi đang chạy tốc độ 3
- **Precondition:** Quạt đã chạy ở tốc độ 3 ít nhất 1 phút.
- **Input:** Nhấn nút Off.
- **Steps:**
  1. Nhấn nút Off
  2. Quan sát cánh quạt cho đến khi dừng hẳn
  3. Ghi lại thời gian cánh dừng
- **Expected:**
  1. Cánh quạt giảm tốc và dừng hẳn
  2. Nút Off giữ nguyên vị trí đã nhấn
  3. Không có tiếng va chạm hoặc tiếng lạ khi dừng

### 01-005 — Nhấn đổi nút liên tục và nhanh
- **Precondition:** Quạt cắm điện, đang tắt.
- **Input:** Nhấn xen kẽ các nút 1, 2, 3, Off khoảng 20 lần trong 10 giây.
- **Steps:**
  1. Nhấn liên tục các nút theo thứ tự 1, 2, 3, Off, lặp lại khoảng 20 lần trong 10 giây
  2. Dừng ở nút tốc độ 2 và quan sát quạt 10 giây
- **Expected:**
  1. Nút không bị kẹt hoặc không nhả
  2. Quạt chạy đúng theo nút được nhấn cuối cùng
  3. Không có tia lửa, mùi khét; cầu dao không nhảy


## Function 02: Vận hành và hiệu năng cơ bản

### 02-001 — Chạy liên tục 30 phút ở tốc độ 3 (nhiệt độ và độ bền)
- **Precondition:** Quạt đặt nơi thoáng, phòng có nhiệt độ bình thường, quạt đang tắt.
- **Input:** Chạy tốc độ 3 liên tục 30 phút.
- **Steps:**
  1. Bật tốc độ 3
  2. Mỗi 10 phút, đặt mu bàn tay lên thân động cơ phía sau 1–2 giây
  3. Ghi nhận tốc độ quay, tiếng ồn và mùi tại mỗi mốc 10, 20, 30 phút
- **Expected:**
  1. Thân động cơ ấm nhưng không nóng đến mức không thể chạm
  2. Không có mùi khét
  3. Tốc độ quay và tiếng ồn ổn định, quạt không tự tắt

### 02-002 — Độ ổn định của đế khi chạy tốc độ 3
- **Precondition:** Quạt đặt trên mặt bàn phẳng, khô.
- **Input:** Chạy tốc độ 3 trong 5 phút.
- **Steps:**
  1. Bật tốc độ 3
  2. Quan sát độ rung và vị trí đế quạt trong 5 phút
- **Expected:**
  1. Quạt không xê dịch trên mặt bàn
  2. Không rung lắc mạnh, không đổ

### 02-003 — Độ ồn theo từng mức tốc độ
- **Precondition:** Phòng yên tĩnh, ứng dụng đo độ ồn trên điện thoại (nếu có), quạt đang tắt.
- **Input:** Tốc độ 1, 2, 3; mỗi mức chạy 1 phút, đo ở khoảng cách 1 m.
- **Steps:**
  1. Bật tốc độ 1, đo và ghi độ ồn (dB) hoặc nghe bằng tai
  2. Lặp lại với tốc độ 2 và tốc độ 3
- **Expected:**
  1. Độ ồn tăng dần theo tốc độ
  2. Không có tiếng rít, cọ xát hoặc gõ lạch cạch ở cả 3 mức

### 02-004 — Lưu lượng và hướng gió theo tốc độ
- **Precondition:** Dải ruy băng hoặc giấy mỏng treo trước quạt, cách 0,5 m, ngang tầm cánh quạt.
- **Input:** Tốc độ 1, 2, 3; mỗi mức chạy 30 giây.
- **Steps:**
  1. Bật tốc độ 1, quan sát dải ruy băng
  2. Lặp lại với tốc độ 2 và tốc độ 3
- **Expected:**
  1. Dải ruy băng bay về phía trước quạt
  2. Mức độ bay tăng dần theo tốc độ

### 02-005 — Chạy lại sau khi mất điện đột ngột
- **Precondition:** Quạt đang chạy ở tốc độ 2.
- **Input:** Rút phích cắm, chờ 10 giây, cắm lại (nút vẫn ở tốc độ 2).
- **Steps:**
  1. Rút phích cắm khi quạt đang chạy tốc độ 2
  2. Chờ 10 giây
  3. Cắm phích lại vào ổ điện, không thao tác nút
- **Expected:**
  1. Quạt tự chạy lại ở tốc độ 2
  2. Không có tia lửa ở phích cắm hoặc ổ điện


## Function 03: An toàn và độ chắc chắn cơ khí

### 03-001 — Lồng bảo vệ chắc chắn và khe hở an toàn
- **Precondition:** Rút phích cắm, quạt tắt.
- **Input:** Lắc nhẹ lồng bằng tay; thử đưa một ngón tay qua khe lưới về phía cánh quạt.
- **Steps:**
  1. Lắc nhẹ lồng trước bằng tay
  2. Kiểm tra các kẹp cố định lồng
  3. Thử đưa một ngón tay qua khe lưới về phía cánh quạt
- **Expected:**
  1. Lồng không lỏng lẻo, các kẹp giữ chắc
  2. Ngón tay không chạm được vào cánh quạt qua khe lưới

### 03-002 — Điều chỉnh góc nghiêng đầu quạt (chỉ thực hiện nếu quạt có chỉnh nghiêng)
- **Precondition:** Rút phích cắm, quạt tắt.
- **Input:** Nghiêng đầu quạt lên xuống ở vài góc khác nhau.
- **Steps:**
  1. Nới núm hoặc khớp nghiêng
  2. Nghiêng đầu quạt lên và xuống ở vài góc
  3. Siết lại, cắm điện và chạy tốc độ 3 trong 1 phút
- **Expected:**
  1. Đầu quạt giữ đúng góc đã chọn khi chạy
  2. Không tự sụp hoặc trượt, khớp không kêu

### 03-003 — Kiểm tra dây điện và phích cắm
- **Precondition:** Rút phích cắm, quạt tắt.
- **Input:** Quan sát và kiểm tra bằng tay vỏ dây, chỗ nối dây, chân phích.
- **Steps:**
  1. Kiểm tra toàn bộ vỏ dây điện
  2. Kiểm tra chỗ dây nối vào thân quạt
  3. Kiểm tra chân phích cắm
- **Expected:**
  1. Vỏ dây không nứt, không hở lõi, không cháy xém
  2. Chỗ nối chắc, không lỏng
  3. Chân phích không cong, không gỉ hoặc đổi màu

### 03-004 — Cánh quạt cân bằng và không chạm lồng
- **Precondition:** Rút phích cắm, quạt tắt.
- **Input:** Quay cánh bằng tay vài vòng; sau đó chạy tốc độ 3.
- **Steps:**
  1. Dùng tay quay cánh quạt vài vòng
  2. Quan sát khe hở giữa cánh và lồng
  3. Cắm điện, chạy tốc độ 3 và quan sát cánh khi quay
- **Expected:**
  1. Cánh quay trơn và không chạm lồng
  2. Cánh không lắc hoặc nghiêng khi chạy
  3. Cánh không nứt, mẻ

### 03-005 — Vận hành trên mặt nghiêng nhẹ (khoảng 10°)
- **Precondition:** Tấm ván nghiêng khoảng 10° đặt ổn định; quạt đặt xa mép; tay sẵn sàng rút phích.
- **Input:** Chạy tốc độ 1 rồi tốc độ 3, mỗi mức 1 phút.
- **Steps:**
  1. Đặt quạt lên mặt nghiêng
  2. Bật tốc độ 1 trong 1 phút, quan sát
  3. Chuyển sang tốc độ 3 trong 1 phút, quan sát
- **Expected:**
  1. Quạt không tự trượt và không đổ
  2. Không có tiếng lạ
