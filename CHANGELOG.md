# Changelog

Tất cả những thay đổi đáng chú ý của dự án kiencang/Book-silaTranslator sẽ được ghi lại trong file này.

Định dạng dựa trên [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
và dự án này tuân thủ [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v1.0.38]- 2026-09-14
### Fixed
- Điều chỉnh tiếp SI tóm tắt theo từng thể loại;

## [v1.0.37]- 2026-09-05
### Fixed
- Cập nhật SI/Prompt tóm tắt chunk tùy theo thể loại tài liệu cần dịch;

## [v1.0.36]- 2026-07-29
### Fixed
- Loại bỏ các chỉ thị phức tạp liên quan đến Latex, chuyển thành dạng đơn giản hơn;
- Chuyển đổi các mã Latex đơn giản thành dạng chỉ số trên (do khi chuyển sang markdown từ PDF, các chỉ số trên lồng Latex vào, ví dụ `$^{12}$`;
- Đầu vào markdown không thể có độ chính xác Latex tuyệt đối nên các chỉ thị không hiệu quả;

## [v1.0.35]- 2026-06-N/A
### Fixed
- Khắc phục tình trạng lỗi do quá trình phân tích markdown làm mất dấu backslash () trước ngoặc nhọn;

## [v1.0.34]- 2026-06-N/A
### Fixed
- Điều chỉnh một chút chỉ thị liên quan đến xử lý công thức toán học mà cú pháp là LaTex.

## [v1.0.33]- 2026-06-12
### Fixed
- Chỉnh lại SI/Prompt tài liệu chuyên ngành, điều chỉnh một số mâu thuẫn, tàn dư do ảnh hưởng của bộ dịch HTML, và bộ dịch Văn học.

## [v1.0.32]- 2026-06-11
### Fixed
- Bổ sung SI/Prompt riêng cho tài liệu khoa học chuyên ngành.

## [v1.0.31]- 2026-06-09
### Fixed
- Loại bỏ hoàn toàn nhiễu của liên kết nội bộ.

## [v1.0.30]- 2026-06-08
### Fixed
- Điều chỉnh lại chỉ thị liên quan đến liên kết nội bộ.

## [v1.0.29]- 2026-06-08
### Fixed
- Thêm yêu cầu để bảo vệ các liên kết nội bộ trong file.

## [v1.0.28]- 2026-05-29
### Fixed
- Thêm mô tả Giọng điệu (Capture Tone) vào phần tóm tắt để giảm ảnh hưởng của đoạn bị cắt giữa chừng.

## [v1.0.27]- 2026-05-19
### Fixed
- Cập nhật sang tiếng Việt SI liên quan đến chuẩn hóa danh sách bảng Đại từ & Tóm tắt khối/chương dịch.

## [v1.0.26]- 2026-05-19
### Fixed
- Thêm chỉ thị bổ sung vào Prompt.

## [v1.0.25]- 2026-05-18
### Fixed
- Cải tiến chất lượng SI/Prompt trích xuất thuật ngữ.

## [v1.0.24]- 2026-05-18
### Fixed
- Điều chỉnh phần trích xuất Đại từ nhân xưng chuẩn hơn.

## [v1.0.23]- 2026-05-17
### Fixed
- Bỏ các tag XML, vì nội dung có thể rỗng, nên các tag XML được cấu trúc luôn trong lệnh xử lý trước khi thế thân vào prompt.

## [v1.0.22]- 2026-05-17
### Fixed
- Chỉnh sửa prompt động, thêm các tag XML để AI phân biệt rõ ràng hơn.
- Sửa file PDF 2 Markdown, bổ sung ngoại lệ không can thiệp ngắt dòng của thơ.
