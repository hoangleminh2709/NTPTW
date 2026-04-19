Phần A:
Câu A1: 01_introduction_html_universe.md, Cuộc hành trình 0.3s xuyên đại dương
1. Khi gõ https://shopee.vn các bước xảy ra: 
- Request xuất phát từ laptop -> đi qua router của nhà
- Qua nhà mạng FPT -> chạy xuyên cáp quang
- Đến data center của Shopee
- Server xử lí request "Tôi muốn thấy giao diện của shopee"
- Response  chạy ngược lại: cáp quang > FPT > router > laptop
- Trình duyệt nhận file HTML, CSS, JS -> render ra giao diện -> Người dùng thấy giao diện

A2: 04_visible_part_html.md, Semantic HTML5 — "Thẻ có ý nghĩa"
Trang web bị Google đánh giá SEO thấp do lạm dụng thẻ div, google không hiểu gì về cấu trúc trang web
4 lỗi semantic:
1.<div class="header"> , ở đây chúng ta thay thẻ div với class là header thành thẻ header luôn
2. tương tự với <div class="footer"> chúng ta thay thẻ div này thành thẻ footer 
3. <div class="main"> thay bằng thẻ main
4. <div class="image"><img src="iphone.jpg"></div> ở trong này thẻ div bọc img cần được thay bằng thẻ figure

A3: 04_visible_part_html.md  Block vs Inline — Hai loại element cơ bản
Hộp 1
Text A Text B
Hộp 2
Text C Text D(in đậm)
Hộp 3
 
Hộp 1,2,3 được 1 mình 1 dòng do thẻ div là thẻ Block(chiếm cả dòng), trong khi Text A Text B chỉ là thẻ span nên chỉ chiếm nội dung(Inline), tương tự với Text C và Text D

A4: 05_tables_hyperlinks.md,  Table — Bảng dữ liệu
<thead> là header: tiêu đề cột
<tbody> là body: dữ liệu chính
<tfoot> là footer: tổng kết

KHÔNG NÊN dùng table để tạo layout trang web vì: 
- table chỉ dùng cho Data tabular
- lỗi thời
- hiện nay đã có Css Grid/Flexbox

PHẦN C:
Quan điểm “dùng <div> cho mọi thứ rồi thêm class là đủ” nghe có vẻ tiện, nhưng về kỹ thuật lại để lại nhiều hệ quả. Thứ nhất là SEO: các công cụ tìm kiếm dựa vào cấu trúc semantic như <header>, <article>, <nav>, <footer> để hiểu nội dung và mức độ quan trọng của từng phần. Nếu tất cả đều là <div>, bạn đang làm mờ “ngữ nghĩa” của trang, khiến việc index và xếp hạng kém hiệu quả hơn. Thứ hai là Accessibility: các trình đọc màn hình (screen readers) dựa vào thẻ semantic để giúp người khiếm thị điều hướng nhanh (ví dụ nhảy giữa các bài viết hoặc menu). Dùng <div> tràn lan buộc bạn phải bổ sung thêm ARIA phức tạp mà vẫn dễ sai sót.

Một ví dụ cụ thể: khi xây blog, nếu bạn dùng <article> cho từng bài và <section> cho từng phần nội dung, công cụ tìm kiếm và screen reader đều hiểu rõ cấu trúc. Ngược lại, dùng toàn <div> khiến mọi thứ chỉ là “khối vô nghĩa”, mất lợi thế tự nhiên mà HTML cung cấp.

Tuy nhiên, không phải lúc nào <div> cũng sai. Trong các trường hợp layout thuần túy (ví dụ wrapper để chia grid, flexbox, hoặc các component UI không mang ý nghĩa nội dung như card container), <div> vẫn hoàn toàn phù hợp. Vấn đề không phải là “cấm dùng <div>”, mà là dùng đúng chỗ: semantic cho nội dung, <div> cho cấu trúc trình bày.
