# Công cụ kết nối thêm (tuỳ chọn)

Lumi đủ để đăng bài, trả lời tin nhắn, gom khách và báo cáo. Các công cụ dưới đây là kết nối (connector) **khác** của AI người dùng, giúp soi đối thủ và làm ảnh nhanh hơn.

Cách gợi ý:
- **Không bắt cài**, không đưa cả danh sách. Chỉ nhắc **một** công cụ đúng lúc người dùng đang cần nó (ví dụ: họ nhờ soi video đối thủ mà chưa có vidIQ).
- Nói rõ công cụ đó làm được gì cho việc đang làm, và có thể tốn phí riêng của công cụ đó (xem trang của họ, không tự báo giá).
- Không có công cụ thì vẫn làm được bằng cách thủ công trong từng skill: đọc trang công khai, nhờ người dùng chụp màn hình, viết lệnh tạo ảnh.

## Bộ khởi đầu (đủ cho đa số chủ shop)
| Công cụ | Giúp gì | Dùng ở skill |
|---|---|---|
| **vidIQ** | Video TikTok / Instagram / YouTube của đối thủ hút xem vượt trội, lời thoại video, nhạc đang thịnh hành | `lumi-soi-doi-thu`, `lumi-tiktok`, `lumi-youtube-shorts`, `lumi-hook-kich-ban` |
| **Canva** | Làm ảnh từ mẫu, điền chữ và ảnh thật, xuất đúng khổ, người dùng tự sửa tay được | `lumi-thiet-ke`, `lumi-anh-bia`, `lumi-instagram` |

## Thêm khi cần
| Công cụ | Giúp gì |
|---|---|
| **Meta Ads** (chính thức của Meta) | Thư viện quảng cáo: quảng cáo đối thủ đang chạy; số liệu quảng cáo của chính người dùng |
| **TikTok for Business** (chính thức của TikTok) | Số liệu và chiến dịch quảng cáo TikTok của người dùng |
| **Adobe** | Chỉnh ảnh chuyên sâu: xoá nền, chỉnh màu, ghép ảnh |
| **Firecrawl** | Đọc website, bảng giá, trang dự án của đối thủ |
| **Descript**, **HyperFrames** | Dựng, cắt video; video có link công khai thì đăng qua Lumi bằng `tai_video_tu_link` |

Cách kết nối: trong Claude vào phần kết nối (Connectors), tìm tên công cụ, bấm kết nối và đăng nhập tài khoản của chính người dùng. ChatGPT / Gemini có mục tương tự hoặc chưa hỗ trợ — khi đó làm theo cách thủ công.

An toàn: chỉ kết nối tài khoản của chính người dùng; công cụ có quyền sửa (quảng cáo, thiết kế) thì vẫn hỏi người dùng trước khi tạo, sửa, chi tiền hay xoá.
