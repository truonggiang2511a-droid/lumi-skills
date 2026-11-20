---
name: lumi-dang-bai
description: Đăng bài, ảnh, video mà chính Claude (hoặc skill của người dùng) vừa làm lên mọi kênh đã nối trong Lumi (Facebook, Instagram, TikTok, YouTube, Threads) qua cổng MCP của Lumi. Dùng khi người dùng nói "đăng lên Lumi", "đăng bài này", "đẩy video này lên fanpage/TikTok", "lên lịch đăng tối nay", hoặc làm xong ảnh/video và muốn đăng. Lumi chỉ làm cầu nối (đăng, chăm khách, quảng cáo); nội dung do AI của người dùng làm.
---

# Lumi – đăng bài

Bạn (AI của người dùng) làm nội dung; Lumi nhận và đăng.

## 0. Kiểm tra kết nối
Gọi `kenh_ket_noi`. Nếu không có công cụ của Lumi, hướng dẫn người dùng nối Lumi MCP **một lần, không cần terminal** (hướng dẫn có hình: https://lumiai.vn/huong-dan):
1. Mở claude.ai → **Plugin** → **Thêm** → **Thêm trình kết nối tùy chỉnh** → tên `Lumi`, URL `https://api.lumiai.vn/mcp` → Kết nối.
2. Trang Lumi hiện ra: đăng nhập, chọn doanh nghiệp, giữ ô **"Cho phép ra lệnh"** → **Cho phép**.
3. Claude Code đăng nhập cùng tài khoản Claude sẽ tự thấy Lumi (gõ `/mcp` để kiểm tra).
Dự phòng khi Claude Code chưa thấy: `claude mcp add --transport http --scope user lumi https://api.lumiai.vn/mcp`, rồi `/mcp` → lumi → Authenticate.
Nếu chỉ thấy công cụ xem mà không có `dang_bai`: kết nối đang ở chế độ chỉ xem, nối lại và giữ ô "Cho phép ra lệnh".

## 1. Chuẩn bị nội dung
- Gọi `thuong_hieu` trước khi viết: giọng văn, điểm mạnh, khách hàng mục tiêu, kho tri thức (bảng giá, ưu đãi, chính sách, câu hỏi khách hay hỏi), bài từng ra khách, bài học AI rút ra. Mục `verified: true` là thông tin chủ doanh nghiệp đã xác nhận.
- Viết bài bằng tiếng Việt, đúng giọng đó, có lời kêu gọi nhắn tin. Không bịa số liệu; chỉ dùng thông tin trong `thuong_hieu` hoặc do người dùng đưa.
- Ảnh: tối đa 10 ảnh, JPG/PNG/WEBP/GIF, mỗi ảnh ≤ 10MB (lớn hơn thì nén bằng ffmpeg trước).
- Video: dọc 9:16 cho Reels/TikTok/Shorts (2 credit/video). **Tự dựng / xuất video thì xuất đúng chuẩn này** để Lumi đăng thẳng, nhanh và nét hơn (không nén lại):
  MP4 (không phải MOV), H.264, yuv420p, 1080×1920, 30 khung hình/giây, khoảng 8–12 Mbps, âm thanh AAC 128–192 kbps, tối đa 48 MB.
  Ví dụ ffmpeg: `ffmpeg -i vao.mov -vf "scale=1080:1920:force_original_aspect_ratio=decrease,pad=1080:1920:(ow-iw)/2:(oh-ih)/2,fps=30" -c:v libx264 -preset slow -crf 20 -maxrate 12M -bufsize 24M -pix_fmt yuv420p -c:a aac -b:a 160k -movflags +faststart ra.mp4`.
  Video sai chuẩn (MOV iPhone, HEVC, quá nặng) Lumi vẫn nhận và tự nén lại, chỉ chậm hơn.
- TikTok bắt buộc có video, Instagram bắt buộc có ảnh hoặc video. Kênh không hợp sẽ bị bỏ qua và báo trong `skipped`.

## 2. Đưa ảnh lên Lumi
- **Ảnh của một sản phẩm đã có trên Lumi**: xem `san_pham` trước; sản phẩm đã có ảnh (`media`) thì dùng luôn các url đó, **không xin người dùng gửi lại**.
- Người dùng gửi ảnh mới của một sản phẩm: đưa lên Lumi (bên dưới) rồi `luu_anh_san_pham` vào đúng sản phẩm (không rõ sản phẩm nào thì hỏi một lần), để lần sau có sẵn. Chưa có công cụ `luu_anh_san_pham` thì bỏ qua bước lưu.
- Ảnh có link công khai: `tai_anh_len` với `url`.
- Ảnh nằm trên máy: `xin_link_tai_anh` → với từng ảnh chạy
  `curl -s -T "<đường dẫn ảnh>" "<put_url>"` → lấy `url` trong kết quả. (Không gửi ảnh dạng base64 qua công cụ: rất tốn ngữ cảnh.)

## 3. Đưa video lên Lumi
Video đã có link công khai (xuất từ Descript, HyperFrames, Canva, hoặc file Google Drive chia sẻ "Bất kỳ ai có đường liên kết"): `tai_video_tu_link` với `url` + `caption`, rồi sang bước 3 bên dưới (đợi `ready`).
Video nằm trên máy (Claude Code):
1. `xin_link_tai_video` với `caption` = nội dung bài, `file_name` = tên file → nhận `put_url`, `content_id`, `upload_id`.
2. `curl -s -T "<đường dẫn video>" "<put_url>"` (thấy `"bytes"` là xong).
3. Gọi `trang_thai_video` mỗi 10 giây (tối đa ~5 phút) tới khi mục có `id = upload_id` báo `ready`. `failed` thì báo lỗi cho người dùng.

## 4. Hỏi lại rồi đăng
- Tóm tắt cho người dùng: nội dung, số ảnh/video, kênh, giờ đăng. Chỉ đăng khi họ đồng ý (trừ khi họ đã bảo "đăng luôn").
- `dang_bai`:
  - chỉ chữ/ảnh: `noi_dung` + `anh` (các url ở bước 2);
  - video: `content_id` (có thể kèm `noi_dung` để sửa lời);
  - `kenh`: id từ `kenh_ket_noi`, bỏ trống = mọi kênh đang hoạt động;
  - `gio_dang`: ISO 8601 có múi giờ, vd `2026-11-18T19:00:00+07:00`; bỏ trống = Lumi chọn khung giờ vàng;
  - `cho_duyet: true` nếu người dùng muốn xem lại trong app Lumi trước khi lên;
  - đăng nhiều trang (từ 5 trang): viết thêm 3–10 cách diễn đạt khác của cùng bài vào `phien_ban` (giữ nguyên số liệu, giá, địa chỉ, lời kêu gọi; đổi câu mở đầu, thứ tự ý, hashtag). Mỗi bản dùng cho đúng một trang, không tốn credit; bản gần trùng bị bỏ; trang không có bản riêng thì Lumi tự viết lại và trừ 1 credit mỗi trang. Đăng rất nhiều trang thì viết càng nhiều bản càng đỡ credit (tối đa 200).
- Lumi tự giãn các trang cách nhau 2 phút để nền tảng không coi là đăng dồn. Kênh đã đủ số bài nền tảng cho phép trong 24 giờ (Instagram 100, Threads 250, TikTok khoảng 15) thì Lumi tự dời bài sang lúc có lượt. Lumi không đăng y hệt một bài lên quá 10 trang.
- Lumi từ chối bài cam kết lợi nhuận, hứa chữa khỏi, có cụm từ cấm của thương hiệu hoặc số điện thoại của khách trong CRM, kèm lý do: sửa đúng chỗ đó rồi gửi lại. Các điểm nên sửa khác Lumi trả về trong `gop_y`.
- Báo lại: trình bày `lich` dạng bảng (ngày · giờ · kênh · định dạng · trạng thái) hoặc hình lịch theo ngày nếu bạn vẽ được, kèm link `xem_lich`; kênh nào bị bỏ qua và vì sao; `gop_y` nói ngắn.
- Ý tưởng định dạng (carousel, Reels, video review bán hàng…), học thương hiệu từ website, nghiên cứu đối thủ: skill `lumi-quy-trinh`, file `references/dinh-dang.md`.

## Đăng lên nhiều trang (từ 10 trang): bộ nội dung xoay vòng
Đổi lời chưa đủ: nền tảng còn nhận ra **cùng một ảnh / video** trên nhiều trang và bớt đề xuất, nặng thì gỡ bài. Thay vì 1 bài cho mọi trang, làm **một bộ nhiều bài khác nhau thật sự** rồi chia cho các nhóm trang.

1. **Lấy nguyên liệu thật:** `thuong_hieu` (giọng văn, điểm mạnh, khách mục tiêu, kho tri thức), `san_pham` (sản phẩm, giá, ảnh thật), `kenh_ket_noi` (danh sách trang). Chỉ dùng thông tin có trong đó hoặc người dùng đưa.
2. **Chia nhóm trang:** mỗi nhóm tối đa khoảng 10 trang; trang cùng khu vực / cùng chủ đề vào chung nhóm.
3. **Làm bộ nội dung:** số bài trong bộ = số nhóm (tối thiểu 3). Mỗi bài khác nhau ở cả ba thứ:
   - **Góc nội dung**, mỗi bài một nguồn trong kho: lợi ích sản phẩm, một câu hỏi khách hay hỏi (faq), bảng giá (price), ưu đãi đang có (offer), xử lý băn khoăn (objection), lời khách thật (testimonial, chỉ mục `verified: true`), mẹo hữu ích, hậu trường.
   - **Hình:** mỗi bài một ảnh / bộ ảnh riêng (ảnh khác nhau của sản phẩm trong `san_pham`, hoặc ảnh người dùng đưa, hoặc ảnh do skill thiết kế của người dùng làm). Không dùng cùng một ảnh cho hai bài trong cùng ngày.
   - **Video:** dựng lại từ cùng tư liệu nhưng khác thật sự: cảnh mở đầu 3 giây đầu khác, câu hook trên hình khác, thứ tự cảnh, ảnh bìa, nhạc khác. Dùng skill dựng video của người dùng (HyperFrames, Descript…) nếu có. Không dùng mẹo lật ngược hình hay đổi tốc độ cho "khác": nền tảng vẫn nhận ra và không giúp đề xuất.
   - Giữ nguyên giá, số liệu, địa chỉ, lời kêu gọi nhắn tin trong mọi bài.
4. **Cho người dùng duyệt:** bảng bài → góc → hình/video → nhóm trang. Đăng khi họ đồng ý.
5. **Đăng:** mỗi bài một lần `dang_bai` với `kenh` = id các trang của nhóm đó, kèm 3–10 `phien_ban` lời khác cho các trang trong nhóm.
6. **Xoay vòng các ngày sau:** dời bộ đi một nhóm (hôm nay bài A cho nhóm 1, bài B cho nhóm 2…; mai bài A cho nhóm 2, bài B cho nhóm 3…), mỗi lần viết `phien_ban` mới. Một bài chỉ quay lại cùng nhóm sau khi đã đi hết các nhóm. Làm theo lịch tuần/tháng thì dùng skill `lumi-lich-noi-dung`.

## Dạy Lumi kiến thức mới
Người dùng đưa bảng giá, ưu đãi, chính sách, câu hỏi thường gặp mới: tách mỗi ý một mục, cho họ xem lại, họ đồng ý thì `them_tri_thuc` từng mục (`loai`: faq, price, offer, policy, objection, testimonial…). Chatbot Lumi trả lời khách dựa vào kho này, bài viết sau cũng dùng. Không lưu thông tin cá nhân của khách.
Giá hay ưu đãi đã đổi: `sua_tri_thuc` (id lấy từ `thuong_hieu`). Mục sai, hết dùng hoặc lẫn ngành khác: hỏi người dùng rồi `xoa_tri_thuc` (xoá hẳn, không khôi phục).

## Lưu ý
- Không đưa số điện thoại, thông tin cá nhân của khách lên ảnh/video.
- Link tải lên hết hạn sau 2 giờ; hết hạn thì xin link mới.
- Muốn xem lịch đã đặt: `bai_dang`. Khách nhắn tới, CRM, quảng cáo: Lumi tự lo, xem bằng `can_duyet`, `khach_hang`, `tong_quan`.
