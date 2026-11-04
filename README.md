# SI-Prompt-Book-EV-Translate
Các SI &amp; Prompt mẫu dùng cho việc dịch sách từ tiếng Anh sang tiếng Việt. 

Bộ trên được ứng dụng trong dự án này: https://github.com/kiencang/silaBook

## Các nhiệm vụ của các cặp SI/Prompt
Ở đây tôi trình bày cụ thể vai trò của từng cặp. SI (system instructions) là chỉ thị hệ thống cho AI được viết rất chi tiết, prompt là lời gợi nhắc, liên kết chặt với SI.

### Phân tích cách chia sách
Nếu cách chia sách theo kiểu thủ công không ưng ý hoặc người dùng chia biết cách chia, họ có thể dùng AI để chia.
- `book_analysis_prompt.md`
- `book_analysis_system_instructions.md`

### Xác định bảng đại từ
Các sách tiểu thuyết, truyện dài hay văn học nói chung có hệ thống xưng hô tương đối phức tạp. Phần này chuyên trách nhiệm vụ phân tích đại từ của từng chunk (phân đoạn/chương) của cuốn sách.
- `pronouns_prompt.md`
- `pronouns_system_instructions.md`

### Chuẩn hóa bảng đại từ
Sau khi có danh sách đại từ của từng chunk, bộ SI này sẽ tổng hợp lại và loại bỏ trùng lặp và cho ra kết quả cuối cùng.
- `normalize_pronouns_prompt.md`
- `normalize_pronouns_system_instructions.md`

### Xác định bảng thuật ngữ
Bất kể loại sách nào, nhưng nhất là sách khoa học có hệ thống các thuật ngữ thường cần dịch thống nhất trên toàn cuốn.
- `glossary_prompt.md`
- `glossary_system_instructions.md`

### Lọc thuật ngữ
Danh sách thuật ngữ có thể từ vài trăm từ đến cả ngàn từ (nếu cuốn sách rất lớn), do vậy việc dịch từng chunk mà chèn cả bảng thuật ngữ vào sẽ thừa thãi rất nhiều.

Bộ bên dưới sẽ lọc ra các thuật ngữ cần thiết (xuất hiện trong chunk cần dịch) để chèn vào, giúp tiết kiệm chi phí AI, nhưng quan trọng hơn là để tránh loãng, phân tán, giúp AI dịch thuật tốt hơn.
- `filter_glossary_prompt.md`
- `filter_glossary_system_instruction.md`

### Dịch theo phong cách khoa học
- `scientific_prompt.md`
- `scientific_system_instructions.md`

### Dịch theo phong cách văn chương
- `multi_prompt.md`
- `multi_system_instructions.md`

### Tóm tắt chunk trước để đưa bối cảnh vào chunk sau
Nó cũng phân theo thể loại:
- Khoa học: `summary_scientific_prompt.md` và `summary_scientific_system_instruction.md`
- Văn chương: `summary_multi_prompt.md` và `summary_multi_system_instruction.md`

Văn chương và tài liệu khoa học khác nhau rất nhiều, vì thế phần cần tóm tắt nội dung ở chunk trước ở 2 thể loại do vậy rất khác nhau.

### Chuyển đổi PDF thành markdown
Với những ai có nhu cầu up trực tiếp file PDF lên công cụ để dịch, công cụ này sẽ chuyển nó thành dạng markdown trước. Nó sử dụng cặp này để chuyển.
- `pdf_to_md_prompt.md`
- `pdf_to_md_system_instruction.md`

Lưu ý là chúng tôi khuyến khích người dùng sử dụng công cụ của bên thứ 3 để chuyển PDF sang markdown vì các lý do sau:
- Chuyển bằng công cụ sẽ tốn token (chi phí);
- Không giữ được ảnh trong bản gốc, bản chuyển đổi chỉ có thuần văn bản;

Người dùng nên dùng các công cụ mạnh và miễn phí để chuyển PDF sang markdown, ví dụ như PaddleOCR hoặc MinierU.
