# Định dạng và công thức nội dung ra khách

Đây là **gợi ý**, không phải luật. Người dùng có skill, công cụ hay phong cách riêng thì dùng của họ. Lumi chỉ từ chối bài cam kết lợi nhuận, hứa chữa khỏi, có cụm từ cấm của thương hiệu hoặc có số điện thoại của khách trong CRM; các điểm khác Lumi trả về trong `gop_y`.

Luôn giữ: một lời mời rõ ràng (nhắn tin, để lại số, đặt lịch) · không bịa giá, số liệu, kết quả, lời khen · không đưa thông tin riêng của khách hàng · đúng giọng văn, màu, logo trong `thuong_hieu`.

## 0. Khi người dùng chưa biết làm gì
1. `thuong_hieu` + `san_pham` (+ `bai_dang` để biết bài nào từng ra khách).
2. Đề xuất **3 phương án**, mỗi phương án: định dạng · góc nội dung · vì sao dễ ra khách · cần tư liệu gì (ảnh thật, video, lời khách).
3. Người dùng chọn → làm → cho duyệt → `dang_bai`.

## 1. Học thương hiệu và website
- `thuong_hieu` trả về `thieu` (mục hồ sơ còn trống). Có link website: đọc trang chủ, trang sản phẩm, giới thiệu, câu hỏi thường gặp → rút ra giọng văn, điểm mạnh, khách mục tiêu, ưu đãi, **màu chính / màu phụ (mã hex), logo, phong cách hình ảnh** (ánh sáng, bố cục, font, kiểu ảnh).
- Tóm tắt cho người dùng duyệt → `sua_thuong_hieu`; giá, chính sách, câu hỏi → `them_tri_thuc`; sản phẩm → `doc_san_pham_tu_link` + `them_san_pham`.
- Logo: tải ảnh lên Lumi (`tai_anh_len`) rồi ghi link vào `logo`.

## 2. Nghiên cứu đối thủ
Xem trang, bài và quảng cáo công khai của 3–5 đối thủ (Thư viện quảng cáo Meta, TikTok). Ghi lại: góc nội dung, định dạng, câu hook, ưu đãi đang chạy. **Học cách làm, không sao chép** chữ, ảnh hay video.

## 3. Ảnh đơn / banner
| Kiểu | Công thức |
|---|---|
| Ảnh thật + 1 câu hook | Ảnh sản phẩm thật, một dòng chữ lớn nói lợi ích hoặc nỗi lo |
| Lợi ích quanh sản phẩm | Sản phẩm ở giữa, 3–4 lợi ích kèm icon xung quanh |
| Trước – sau | Hai nửa so sánh (chỉ ảnh thật, khách đã đồng ý) |
| Giá / ưu đãi | Giá lớn, hạn ưu đãi, nút "Nhắn ngay" |
| Lời khách thật | Ảnh khách hoặc tin nhắn đã che thông tin + câu khen (chỉ mục đã xác nhận) |
| Bảng so sánh | 2–3 lựa chọn cạnh nhau |
| Hậu trường | Đội ngũ, kho, quy trình làm |
Chữ trên ảnh 7–10 từ · đúng màu và logo · 4:5 cho bảng tin, 9:16 cho story.

## 4. Carousel (đăng nhiều ảnh trong một bài)
| Kiểu | Cấu trúc |
|---|---|
| Vấn đề → giải pháp | 1 nỗi lo → 2–3 vì sao → 4–6 giải pháp / sản phẩm → 7 lời mời |
| "5 điều cần biết" | 1 tiêu đề → 2–6 mỗi slide một ý → 7 lời mời |
| Tham quan / review từng phần | 1 ảnh đẹp nhất + giá → 2–8 từng góc → cuối: vị trí, lời mời |
| So sánh A hay B | 1 câu hỏi → 2–4 từng tiêu chí → 5 ai hợp cái nào → 6 lời mời |
| Hướng dẫn từng bước | 1 kết quả cuối → 2–6 từng bước → 7 "cần làm giúp? nhắn tin" |
| Câu hỏi khách hay hỏi | mỗi slide một câu hỏi + trả lời (lấy từ kho tri thức) → lời mời |
Slide 1 quyết định có ai trượt tiếp · mỗi slide một ý · slide cuối có lời mời. Gửi các ảnh theo đúng thứ tự trong `anh`.

## 5. Reels / TikTok / Shorts
| Kiểu | Khung dựng |
|---|---|
| Hook – Giá trị – Lời mời | 0–3s hook bằng hình + chữ → 3 ý / cảnh giá trị → lời mời |
| Tham quan nhanh | cảnh đẹp nhất trước → mỗi phòng / góc 1–2s, chữ ngắn → giá + lời mời |
| POV / tình huống | "POV: bạn vừa…" → tình huống thật → sản phẩm giải quyết |
| Sai lầm thường gặp | "Đừng mua … khi chưa xem" → 3 sai lầm → cách đúng |
| Trước – sau | cảnh trước → chuyển cảnh → cảnh sau → lời mời |
| Trả lời bình luận | câu hỏi thật của khách mở đầu → trả lời bằng video |
| Theo xu hướng | ghép sản phẩm vào trào lưu (âm thanh có sẵn trong app nền tảng cho đúng bản quyền) |
3 giây đầu có chuyển động hoặc câu gây tò mò · luôn có phụ đề · 15–45 giây · xuất MP4 H.264 1080×1920 (thông số trong skill `lumi-dang-bai`).

## 6. Video review bán hàng (chuyển đổi cao)
| Công thức | Các bước |
|---|---|
| PAS | nỗi lo → khuấy (phiền thế nào) → sản phẩm giải quyết, cảnh thật → lời mời |
| AIDA | gây chú ý → khơi tò mò → khiến muốn có → hành động |
| Review thật 5 điểm | mở hộp / mở cửa → 3 điểm thích → 1 điểm cần lưu ý (tăng tin tưởng) → ai nên mua → lời mời |
| So sánh giá trị | "cùng tầm giá, cái này hơn ở…" → 3 điểm hơn → lời mời |
| Một ngày dùng thử | dùng trong đời thật → cảm nhận → kết quả có thật |
| Người dẫn chuyên gia | nói thẳng vào camera: kinh nghiệm, mẹo → giới thiệu |
| Video giải thích | câu hỏi lớn → hình minh hoạ / sơ đồ từng bước → kết luận → lời mời |
**Bất động sản:** mặt tiền → lối vào → phòng khách → bếp → phòng ngủ → ban công / sân thượng → khu xung quanh (flycam nếu có) → giá, pháp lý (chỉ khi đã xác nhận) → lời mời. Chữ trên hình: diện tích, hướng.

## 7. Thử A/B và học lại
1. Mỗi tuần 1–2 cặp: cùng sản phẩm, khác **một thứ** (hook, carousel hay Reels, ảnh bìa, giờ đăng), đăng lên 2 nhóm trang tương đương.
2. Sau 48–72 giờ so số tin nhắn và khách để số (CRM, link nhắn tin có mã theo dõi của từng bài) — không chỉ lượt thích.
3. Giữ kiểu thắng, bỏ kiểu thua; điều rút ra nói với người dùng và đưa vào hướng dẫn thương hiệu.
4. Tuần sau làm thêm theo kiểu thắng + thử một biến thể mới.

## 8. Đăng xong
Trình bày `lich` mà `dang_bai` trả về: bảng **ngày · giờ · kênh · định dạng · trạng thái** (hoặc hình lịch theo ngày, mỗi kênh một màu, nếu bạn vẽ được), kèm link `xem_lich`. Có `gop_y` thì nói ngắn cách làm tốt hơn lần sau.
