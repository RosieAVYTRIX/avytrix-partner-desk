<div align="center">

# RosieAVYTRIX Partner Desk
### Kết nối hôm nay. Hợp tác ngày mai.

Một workspace nhỏ để theo dõi cơ hội hợp tác, giai đoạn và bước tiếp theo.

[← Portfolio RosieAVYTRIX](https://rosieavytrix.github.io/)

**[Mở bản chạy thử ↗](https://rosieavytrix.github.io/avytrix-partner-desk/)** · [Project Brief](https://rosieavytrix.github.io/avytrix-project-brief/) · [Đề xuất hợp tác](https://github.com/RosieAVYTRIX/RosieAVYTRIX/issues/new)

</div>

> Demo portfolio của RosieAVYTRIX, phát triển với sự hỗ trợ của Codex. Sáu cơ hội, tên nhóm và giá trị ban đầu đều là dữ liệu minh họa; không đại diện khách hàng, hợp đồng hay doanh thu thực tế.

## Vì sao có Partner Desk?

Sau một cuộc trò chuyện, cơ hội hợp tác dễ bị rơi vào những ghi chú rời rạc: đã trao đổi đến đâu, lần tới làm gì, ngày nào cần liên hệ lại? Partner Desk đưa ba câu hỏi đó lên một màn hình gọn, đủ để minh họa trải nghiệm quản lý quan hệ đối tác.

Dự án bổ sung cho **RosieAVYTRIX Project Brief**: Project Brief giúp thống nhất đề bài; Partner Desk giúp theo dõi cơ hội và hành động tiếp theo. Hai demo có liên kết điều hướng, chưa đồng bộ dữ liệu với nhau.

## Trải nghiệm trong 60 giây

1. Xem 6 cơ hội mẫu và tổng quan bên trên.
2. Tìm `may` hoặc chọn **Khám phá** để lọc dữ liệu.
3. Bấm vào một cơ hội để sửa giai đoạn, giá trị dự kiến, ngày theo dõi hoặc ghi chú.
4. Chọn **Thêm cơ hội** để tạo bản ghi của bạn.
5. Chọn **Xuất CSV** để tải danh sách theo bộ lọc hiện tại.

Nháp được lưu trên trình duyệt. Dùng **Xóa dữ liệu** để bắt đầu workspace trống; **Nạp lại mẫu** thay thế toàn bộ bản ghi bằng dữ liệu minh họa, sau bước xác nhận.

## Nhận diện thương hiệu

Tên giao diện, nội dung xuất và liên kết GitHub đã đồng bộ thành **RosieAVYTRIX**. Bản demo chính thức chạy miễn phí trên GitHub Pages dưới tên `rosieavytrix.github.io`. Nháp lưu trên trình duyệt tại hostname cũ không tự chuyển sang hostname mới.

## Tính năng

- Tạo, chỉnh sửa và xóa cơ hội; 5 giai đoạn từ mới kết nối đến đã thống nhất hoặc tạm dừng.
- Ghi người/nhóm đối tác, dự án, giá trị dự kiến, bước tiếp theo, ngày theo dõi và ghi chú.
- Tìm kiếm tiếng Việt có hoặc không dấu; lọc giai đoạn và sắp xếp theo ngày, giá trị hoặc tên.
- Tổng quan số cơ hội, cơ hội đang mở, hành động đến hạn và tổng giá trị dự kiến của cơ hội mở.
- CSV UTF-8 có BOM để thuận tiện mở bằng công cụ bảng tính; xử lý dấu phẩy, dấu nháy, xuống dòng và tiền tố công thức.
- Giao diện desktop dạng hàng; điện thoại dạng thẻ, hộp thoại cuộn và nút lưu luôn ở cuối vùng nhìn.
- Không cần tài khoản, API key hoặc thư viện JavaScript ngoài.

## Chạy trên máy

Cần Python 3 cho HTTP server. Node.js 18+ chỉ cần khi chạy kiểm tra.

```bash
git clone https://github.com/RosieAVYTRIX/avytrix-partner-desk.git
cd avytrix-partner-desk
python3 -m http.server 4174 --directory dist
```

Mở http://localhost:4174. Không mở trực tiếp HTML vì ứng dụng dùng ES modules.

```bash
npm test
```

Không cần `npm install`.

## Cấu trúc

```text
dist/
  index.html       Workspace, bộ lọc và biểu mẫu
  style.css        Thiết kế responsive và hộp thoại mobile
  app.js           CRUD, render an toàn, lưu nháp và xuất file
  model.js         Giai đoạn, dữ liệu mẫu, tổng hợp, tìm kiếm và CSV
  icon.svg         Biểu tượng RosieAVYTRIX
tests/
  model.test.js    Kiểm tra logic dữ liệu
.github/workflows/
  ci.yml           Chạy kiểm tra trên push / pull request
```

HTML/CSS/JavaScript thuần giữ bản demo dễ đọc và triển khai bằng static hosting. Logic dữ liệu tách khỏi DOM để kiểm tra độc lập. Nội dung người dùng hiển thị qua `textContent`, không nội suy vào HTML. Dữ liệu khôi phục được chuẩn hóa và giới hạn trường trước khi sử dụng.

## Cách tính tổng quan

- **Đang trao đổi:** Mới kết nối, Khám phá hoặc Đề xuất.
- **Cần theo dõi:** Cơ hội đang trao đổi có ngày theo dõi đến hôm nay hoặc trước đó, theo ngày trên thiết bị.
- **Giá trị dự kiến:** Tổng giá trị của cơ hội đang trao đổi; không tính Đã thống nhất và Tạm dừng. Đây không phải doanh thu hoặc dự báo có trọng số.
- Bộ lọc chỉ ảnh hưởng danh sách và CSV; các số tổng quan luôn phản ánh toàn bộ workspace.

## Kiểm chứng

Bốn kiểm tra tự động bao phủ tổng quan, tìm kiếm không dấu kết hợp giai đoạn, CSV và khôi phục dữ liệu lỗi. GitHub Actions chạy cùng bộ kiểm tra.

Kiểm tra trình duyệt: tạo cơ hội, sửa giai đoạn, tổng quan cập nhật, khôi phục sau tải lại, tìm kiếm không dấu, bộ lọc, xóa bản ghi thử và tải CSV theo bộ lọc. Bố cục được đo tại 320, 360, 390, 430, 768 và 1280px, không có cuộn ngang. Đây là viewport mô phỏng, chưa thay thế thử nghiệm trên thiết bị iOS/Android thật.

## Dữ liệu & giới hạn

- Nội dung biểu mẫu lưu trong localStorage trên cùng trình duyệt, không gửi đến backend, không đồng bộ thiết bị.
- Font tải từ Google Fonts; font hệ thống được dùng khi không tải được.
- Ngày đến hạn phụ thuộc ngày/giờ trên thiết bị; ứng dụng không gửi thông báo hoặc email nhắc việc.
- Chưa có đăng nhập, phân quyền, nhiều người cùng sửa, nhập lại CSV hoặc tích hợp CRM.
- CSV là bản xuất; chưa có tính năng khôi phục tự động từ CSV.
- Xóa dữ liệu trình duyệt có thể làm mất nháp. Xuất CSV trước khi xóa hoặc nạp lại mẫu.
- Demo không cung cấp cam kết thời hạn, báo giá hoặc xác nhận hợp đồng.

## Hướng phát triển

- Nhập và đối chiếu dữ liệu CSV.
- Backend có xác thực, phân quyền và lịch sử chỉnh sửa.
- Liên kết brief với cơ hội sau khi thống nhất cách lưu và chia sẻ dữ liệu.

## Hợp tác cùng RosieAVYTRIX

[Chia sẻ bài toán của bạn](https://github.com/RosieAVYTRIX/RosieAVYTRIX/issues/new): quy trình hiện tại, người sử dụng, kết quả mong muốn và phạm vi thử nghiệm.

## Xuất bản với GitHub Pages

GitHub Actions chạy `npm test`, đóng gói riêng thư mục `dist/` và triển khai lên GitHub Pages sau mỗi thay đổi mã nguồn trên `main`. Trong Settings → Pages, nguồn xuất bản là **GitHub Actions**. Các đường dẫn asset dùng đường dẫn tương đối để chạy được dưới đường dẫn repo.

## Giao diện thống nhất

Dark mode graphite–champagne dùng chung giữa portfolio và hai demo. Nút portfolio và demo điều hướng trong cùng tab; các liên kết mã nguồn vẫn mở tab mới khi có chỉ định. Bản in Project Brief có nền sáng riêng.
