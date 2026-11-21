---
name: lumi-anh-bia
description: Lên ý tưởng và viết brief ảnh bìa / ảnh bài đăng cho doanh nghiệp - ảnh bìa YouTube, ảnh bìa Reels / TikTok / Shorts, ảnh bài Facebook, slide đầu carousel Instagram - với 2–3 phương án để thử, chữ trên ảnh ngắn, màu thương hiệu từ Lumi, rồi viết sẵn lệnh tạo ảnh cho ChatGPT / Gemini / Canva và đăng ảnh qua Lumi. Dùng khi người dùng nói "làm ảnh bìa", "thumbnail", "ảnh cho bài này", "ảnh bìa video", "banner bài đăng".
---

# Lumi – ảnh bìa và ảnh bài đăng

Skill này viết **chữ và hướng dẫn**. Người dùng đã kết nối Canva hoặc Adobe thì bạn làm luôn ảnh theo phương án đã chọn (skill `lumi-thiet-ke`, mục 4); không có thì người dùng tạo ảnh bằng ChatGPT (ảnh), Gemini, Canva hoặc nhờ thiết kế, rồi đưa ảnh lên Lumi.
Ưu tiên **ảnh thật** của sản phẩm (từ `san_pham` hoặc người dùng chụp): ảnh thật thường đáng tin hơn ảnh AI.
Nguyên tắc chung để ảnh không "nhìn là biết AI" và bảng kiểm tra trước khi đăng: skill `lumi-thiet-ke`.

Không thấy công cụ của Lumi: hướng dẫn nối Lumi MCP theo https://lumiai.vn/huong-dan.

## 0. Lấy nguyên liệu thật
`thuong_hieu` (màu chính / màu nhấn trong `colors`, logo, phong cách hình ảnh, từ cấm), `san_pham` (ảnh thật, giá, điểm nổi bật), tiêu đề hoặc nội dung bài / video sẽ đi kèm.
**Không bịa** kết quả, con số, lời hứa trên ảnh. Không đưa **số điện thoại** lên ảnh. Không dùng gương mặt người thật khi người đó chưa đồng ý; không tạo ảnh AI giả làm khách hàng thật.

## 1. Chọn loại ảnh và khổ
| Dùng cho | Khổ | Ghi chú |
|---|---|---|
| Ảnh bìa video YouTube (video ngang) | 1280×720 (16:9) | Đặt trong YouTube Studio; Lumi chưa đặt ảnh bìa YouTube thay người dùng |
| Ảnh bìa Shorts / Reels / TikTok | 1080×1920 (9:16) | Thường chọn khung hình trong video hoặc tải ảnh bìa trong app của nền tảng: đặt cảnh đẹp nhất ở giây đầu video |
| Ảnh bài Facebook | 1080×1350 (4:5) hoặc 1200×630 | Ảnh dọc chiếm nhiều màn hình hơn khi lướt |
| Slide đầu carousel / ảnh Instagram | 1080×1350 (4:5) | Slide 1 là lời hứa của cả carousel (skill `lumi-instagram`) |

## 2. Chia việc với tiêu đề
Ghi rõ: tiêu đề / dòng đầu bài **đã nói gì**, ảnh **mang phần còn lại** (kết quả, cảm xúc, vật thể, con số). Ảnh **không lặp chữ của tiêu đề**: chữ khác, cùng lời hứa.

## 3. Quy tắc bắt buộc
- **Một điểm nhìn chính**: một gương mặt có cảm xúc thật, hoặc một vật / kết quả (căn nhà, phòng khách, sản phẩm). Hai thứ tranh nhau thì người xem không biết nhìn đâu.
- **Chữ trên ảnh tối đa 3–5 chữ**, là cụm gây tò mò, không phải câu văn. Ví dụ: "Trả trước 1,2 tỷ", "Cách chợ 500m", "Nhà thô → thế này".
- **Hai màu chủ đạo**: màu chính của thương hiệu + một màu nhấn tương phản mạnh. Nền tách rõ khỏi chủ thể.
- **Đọc được ở cỡ nhỏ** (khoảng 120–320 px chiều ngang, cỡ trên điện thoại): nheo mắt nhìn vẫn thấy chữ và chủ thể.
- Ảnh bìa YouTube: không đặt chữ / logo ở góc dưới bên phải (bị số phút che).
- Cảm xúc trên mặt phải khớp nội dung (video bình tĩnh mà mặt hốt hoảng là hứa sai).

## 4. Viết 2–3 phương án
Mỗi phương án khác nhau ở **một thứ lớn** (mặt người hay căn nhà, có chữ hay không, màu nền), để dễ biết cái nào hiệu quả. Mỗi phương án ghi:
```
PHƯƠNG ÁN [A/B/C]: [tên] — góc bán: […]
Khổ: [...]
Chủ thể chính: [ảnh thật nào / cảnh gì, chiếm bao nhiêu khung, hướng nhìn]
Chữ trên ảnh: "[3–5 chữ]" — vị trí: [...]
Màu: chính [mã màu], nhấn [mã màu], nền [mã màu / cách xử lý]
Chi tiết phụ: [mũi tên / con số / logo nhỏ / không]
Kiểm tra cỡ nhỏ: [cái gì phải còn đọc được]
```
Đề xuất phương án nên dùng trước và vì sao. Hỏi người dùng: "Chọn phương án nào, hay sửa gì?"

## 5. Viết lệnh tạo ảnh
Sau khi người dùng chọn, viết lệnh (prompt) trong khối code để họ dán vào ChatGPT ảnh / Gemini, hoặc các bước làm trong Canva:
```
Dùng ảnh tôi gửi kèm [ảnh căn nhà / sản phẩm / chân dung đã đồng ý]. Tạo ảnh [khổ, kích thước].
Bố cục: [chủ thể ở đâu, chiếm bao nhiêu khung].
Chữ: "[cụm chữ]" — chữ đậm không chân, màu [mã], viền [màu] để đọc rõ, đặt ở [vị trí].
Màu: chính [mã], nhấn [mã], nền [mã, phẳng / chuyển màu / làm mờ cảnh].
Giữ nguyên chi tiết thật của [căn nhà / sản phẩm], không thêm thứ không có thật.
Không có số điện thoại, không có chữ nhỏ, chữ đọc được khi ảnh rộng 320px.
```
Ghi chú: chữ tiếng Việt có dấu đôi khi bị AI vẽ sai; nếu sai thì để AI làm ảnh không chữ rồi thêm chữ trong Canva.

## 6. Kiểm tra ảnh rồi đăng qua Lumi
1. Người dùng gửi ảnh đã làm: mở xem ở cỡ thật và cỡ nhỏ; kiểm tra đúng chữ (dấu tiếng Việt), khổ, không bị cắt, màu thương hiệu, không có thông tin sai hay số điện thoại. Sai thì sửa lệnh và làm lại.
2. Ảnh bài đăng: đưa lên Lumi (`tai_anh_len` với link, hoặc `xin_link_tai_anh` cho ảnh trên máy), rồi đăng theo skill `lumi-fanpage` / `lumi-instagram` / `lumi-dang-bai`.
3. Ảnh bìa YouTube / Reels / TikTok: hướng dẫn người dùng tự đặt trong YouTube Studio hoặc app của nền tảng sau khi video lên.

## Nguồn
Phát triển từ youtube-thumbnail trong [social-media-skills](https://github.com/charlie947/social-media-skills) của Charlie Hills và yt-thumbnail-brief trong [youtube-skills](https://github.com/sergebulaev/youtube-skills) của Sergey Bulaev
(cùng giấy phép MIT, bản gốc ở `LICENSE-goc.txt`), viết lại cho doanh nghiệp Việt và Lumi; bỏ bước tải ảnh bìa qua Publora của bản gốc.
