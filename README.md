# SI-Prompt-Book-EV-Translate
Các SI &amp; Prompt mẫu dùng cho việc dịch sách từ tiếng Anh sang tiếng Việt. 

Bộ trên được ứng dụng trong dự án này: https://github.com/kiencang/silaBook

## Các model AI khuyến nghị sử dụng
Không có model AI cụ thể được khuyến nghị, vì mức độ thay đổi của AI rất nhanh. Lời khuyên chung là bạn nên chọn model AI tầm trung trở lên và dù chọn model AI nào thì việc kiểm thử kết quả đầu ra là điều luôn luôn phải thực hiện.

Và dù không chỉ định model AI cụ thể nào, tôi nhận thấy các model AI của Gemini, OpenAI và Claude có tiềm năng cho kết quả tốt nhất.

Việc phát triển các SI/Prompt này được thực hiện trên Gemini, và nó hoạt động tương đối tốt với Gemini Flash. Thử với bản Pro hoặc Argon cũng cho kết quả khả quan. 

Các dòng Lite của Gemini không đủ sức mạnh để thực hiện việc dịch trực tiếp, và nói chung các model AI yếu tương tự chỉ phù hợp thực hiện một tác vụ nhẹ nhàng, ví dụ như để xác định cách chia khối sách, hoặc tóm tắt một đoạn đã dịch.

## Các nhiệm vụ của các cặp SI/Prompt
Ở đây tôi trình bày cụ thể vai trò của từng cặp. SI (System Instructions) là chỉ thị hệ thống cho AI được viết rất chi tiết, Prompt là lời gợi nhắc, liên kết chặt với SI.

### Phân tích cách chia sách
Nếu cách chia sách theo kiểu thủ công không ưng ý hoặc người dùng chưa biết cách chia, họ có thể dùng AI để chia.

- `book_analysis_prompt.md`
- `book_analysis_system_instructions.md`

Ở giao diện sử dụng của công cụ, để tiết kiệm chi phí, người dùng không cần đưa toàn bộ sách vào phân tích. Họ có thể lấy mẫu 25% hoặc 50%.

### Xác định bảng đại từ
Các sách tiểu thuyết, truyện dài hay văn học nói chung có hệ thống xưng hô tương đối phức tạp. Phần này chuyên trách nhiệm vụ phân tích đại từ của từng chunk của cuốn sách theo ngưỡng mặc định là 10 ngàn từ.

- `pronouns_prompt.md`
- `pronouns_system_instructions.md`

### Chuẩn hóa bảng đại từ
Sau khi có danh sách đại từ của từng chunk 10 ngàn từ, bộ SI này sẽ tổng hợp lại và loại bỏ trùng lặp và cho ra kết quả chuẩn cuối cùng.

- `normalize_pronouns_prompt.md`
- `normalize_pronouns_system_instructions.md`

### Xác định bảng thuật ngữ
Bất kể loại sách nào, nhưng nhất là sách khoa học, chúng có hệ thống các thuật ngữ thường cần dịch thống nhất trên toàn cuốn.

- `glossary_prompt.md`
- `glossary_system_instructions.md`

Bộ trên sẽ giúp xác định các thuật ngữ, từ loại và ý nghĩa tiếng Việt của nó. Công cụ sau đó tự tổng hợp lại và loại bỏ các từ trùng lặp dựa trên từ gốc tiếng Anh và từ loại, điều này sẽ tiết kiệm hơn và vẫn có độ chính xác rất cao thay vì cần thêm một bộ chuẩn hóa (giống như chuẩn hóa bảng đại từ).

### Lọc thuật ngữ
Danh sách thuật ngữ có thể từ vài trăm từ đến cả ngàn từ (nếu cuốn sách rất lớn), do vậy việc dịch từng chunk mà chèn cả bảng thuật ngữ đầy đủ vào sẽ thừa thãi rất nhiều.

Bộ bên dưới sẽ lọc ra các thuật ngữ cần thiết (xuất hiện trong chunk cần dịch) để chèn vào, giúp tiết kiệm chi phí AI, nhưng quan trọng hơn là để tránh loãng, phân tán, giúp AI dịch thuật tập trung hơn.

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
