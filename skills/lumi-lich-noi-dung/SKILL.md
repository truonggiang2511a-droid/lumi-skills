---
name: lumi-lich-noi-dung
description: Lên lịch nội dung cả tuần hoặc cả tháng (7 hoặc 30 bài) rồi xếp lịch qua Lumi MCP để Lumi tự đăng mỗi ngày lên mọi trang. Dùng khi người dùng nói "lên lịch tuần/tháng", "làm nội dung cả tháng", "mỗi ngày 1 bài", "đăng đều đặn", "kế hoạch nội dung", "lịch đăng 30 ngày".
---

# Lumi – lịch nội dung tuần / tháng

Bạn (AI của người dùng) ngồi một lần làm cả lô bài; Lumi giữ lịch và **tự đăng mỗi ngày** trên máy chủ (người dùng không cần mở máy). Không cần hẹn giờ chạy lại AI.

## 1. Chuẩn bị
- `thuong_hieu`: giọng văn, điểm mạnh, khách mục tiêu, bảng giá / ưu đãi (chỉ dùng mục có thật), bài từng ra khách.
- `san_pham`: sản phẩm, giá, ảnh thật để làm hình cho từng bài.
- `kenh_ket_noi`: các trang sẽ đăng. Từ 5 trang trở lên thì mỗi bài cần 3–5 `phien_ban`. Từ 10 trang trở lên thì chia nhóm trang và làm bộ nội dung xoay vòng (mục 2b).
- `bai_dang`: lịch đã có, để không trùng ngày / trùng chủ đề.
- Hỏi người dùng nếu chưa rõ: sản phẩm chính, số bài mỗi ngày (mặc định 1), giờ đăng (mặc định khung giờ vàng của từng trang), có cần chờ duyệt không (mặc định chờ duyệt).

## 2. Lập kế hoạch trước, viết sau
1. Đưa người dùng bảng: ngày → góc nội dung → tiêu đề. Xoay vòng các góc: lợi ích, câu hỏi khách hay hỏi, so sánh, câu chuyện khách thật (chỉ khi có trong thương hiệu), ưu đãi đang có, hậu trường, mẹo hữu ích, video ngắn.
2. Viết đầy đủ 3 bài làm mẫu để người dùng duyệt giọng văn.
3. Người dùng đồng ý → viết đủ cả lô. Không bịa giá, số liệu, lời khen của khách.

## 2b. Nhiều trang (từ 10 trang): xoay vòng theo nhóm
- Chia trang thành nhóm khoảng 10 trang (cùng khu vực / chủ đề chung nhóm). Mỗi ngày làm số bài = số nhóm; mỗi bài một góc nội dung, một ảnh / video riêng (cách làm trong skill `lumi-dang-bai`, mục "bộ nội dung xoay vòng").
- Lịch dạng bảng: ngày × nhóm trang → bài. Ngày sau dời bộ đi một nhóm để nhóm nào cũng lần lượt có mọi bài, mỗi lần lời mới (`phien_ban` mới).
- Cùng một ảnh / video không lên hai nhóm trong cùng ngày. Một bài quay lại cùng nhóm chỉ sau khi đã đi hết các nhóm.
- Ít ảnh / video: hỏi người dùng thêm tư liệu, hoặc giãn lịch (mỗi nhóm 1 bài mỗi 2 ngày), không dùng lặp một hình cho mọi trang.

## 3. Xếp lịch qua Lumi
- Mỗi bài một lần `dang_bai`: `kenh` = các trang của nhóm nhận bài đó (bỏ trống = mọi trang, chỉ khi dưới 10 trang), `noi_dung`, `gio_dang` = ngày của bài (ISO 8601 có múi giờ +07:00, ví dụ `2026-11-20T19:00:00+07:00`), `phien_ban` nếu nhiều trang, `cho_duyet: true` trừ khi người dùng bảo đăng thẳng.
- Có ảnh / video: đưa lên trước (`tai_anh_len`, `xin_link_tai_anh`, `tai_video_tu_link`, `xin_link_tai_video`) rồi gắn vào đúng bài.
- Bài cần video mà chưa có video: vẫn xếp bài chữ / ảnh cho Facebook, báo người dùng TikTok sẽ bỏ qua bài đó.

## 4. Báo lại
- Tổng số bài đã xếp, từ ngày nào tới ngày nào, trên những kênh nào; bài nào bị bỏ qua và vì sao.
- Nhắc: bài chờ duyệt nằm trong app Lumi → Lịch đăng (duyệt cả tuần một lần là xong). Lumi gửi báo cáo mỗi sáng qua Telegram / app.

## Lưu ý
- Lô 30 bài dài: làm theo từng tuần (7 bài một đợt) nếu cuộc trò chuyện quá dài.
- Muốn đổi bài đã xếp: xem `bai_dang`, báo người dùng huỷ / sửa trong app.
