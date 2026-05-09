A1:
1. type="email" → Ô nhập text, tự kiểm tra có @ → Dùng cho form đăng ký
2. type="password" → Các ký tự nhập vào sẽ bị ẩn đi (thay bằng dấu chấm hoặc dấu sao) → Dùng cho ô nhập mật khẩu khi đăng nhập hoặc xác nhận thanh toán.
3. type = "text" -> 1 ô trống hình chữ nhật, không có validation mặc định -> dùng cho các trường thông tin không có định dạng chuẩn như: Nhập tên sản phẩm cần tìm, nhập họ tên người mua,..
4. type = "checkbox" -> Ô vuông nhỏ để tích chọn (cho phép chọn nhiều giá trị cùng lúc) → Dùng trong bộ lọc thuộc tính sản phẩm (ví dụ: chọn cùng lúc Size L, XL và màu Đen)
5. type = "radio" -> Một nút tròn nhỏ. Khi được chọn, tâm nút sẽ được lấp đầy. Các nút radio có cùng thuộc tính name sẽ tạo thành một nhóm, trong đó tại một thời điểm chỉ có duy nhất một nút được chọn. Nếu có thuộc tính required trong nhóm, trình duyệt sẽ báo lỗi nếu người dùng nhấn "Submit" mà chưa chọn bất kỳ tùy chọn nào. -> họn phương thức thanh toán: Người dùng chỉ được chọn một trong các hình thức: "Thanh toán khi nhận hàng (COD)", "Chuyển khoản ngân hàng", hoặc "Ví điện tử".
6. type = "color" -> Hiển thị bảng chọn màu sắc (color picker) của hệ điều hành -> Dùng trong công cụ tùy biến sản phẩm (như thiết kế áo thun hoặc chọn màu nội thất).
7. type = "button" -> Một nút bấm hình chữ nhật (giao diện mặc định tùy hệ điều hành), bên trong hiển thị nội dung của thuộc tính value. -> Validation tự động: Không có. Bản thân nút này không kiểm tra dữ liệu, nó chỉ đợi được nhấn (click). -> Áp dụng mã giảm giá: Sau khi khách nhập code vào ô type="text", họ nhấn nút này để hệ thống kiểm tra mã mà không cần tải lại toàn bộ trang thanh toán.
8. type = "date" -> Hiển thị giao diện chọn ngày (calendar picker) tùy theo trình duyệt -> Dùng để chọn ngày dự kiến nhận hàng hoặc chọn ngày sinh để nhận ưu đãi thành viên.
9. type = "number" → Ô nhập số kèm hai nút mũi tên tăng/giảm ở góc; tự động báo lỗi nếu nhập chữ hoặc nằm ngoài khoảng min/max → Dùng để chọn số lượng sản phẩm muốn thêm vào giỏ hàng.
10. type = "file" → Hiển thị nút "Choose File" để mở cửa sổ chọn tệp tin từ máy tính/điện thoại; có thể giới hạn định dạng ảnh bằng thuộc tính accept → Dùng để khách hàng tải ảnh thực tế sản phẩm khi viết đánh giá (Review).

A2:
<!-- Trường hợp 1 -->
<input type="text" required value="">   <!-- User để trống -->
Trình duyệt chặn lại, không cho gửi form và hiển thị thông báo nhắc nhở do thuộc tính required là bắt buộc người dùng không được để trống trường này. 

<!-- Trường hợp 2 -->
<input type="email" value="abc">        <!-- User gõ "abc" -->
Trình duyệt chặn lại, hiển thị thông báo lỗi yêu cầu nhập đúng định dạng email do thiếu @ do type = "email" yêu cầu dữ liệu phải tuân thủ cấu trúc của 1 email hợp lệ(bao gồm @). 

<!-- Trường hợp 3 -->
<input type="number" min="1" max="10" value="15"> <!-- User gõ 15 -->
Trình duyệt sẽ chặn lại và báo lỗi yêu cầu giá trị phải nhỏ hơn hoặc bằng 10 do dữ liệu 15 đã vượt max 10

<!-- Trường hợp 4 -->
<input type="text" pattern="[0-9]{10}" value="abc123"> <!-- User gõ "abc123" -->
Trình duyệt sẽ chặn lại và yêu cầu người dùng nhập đúng định dạng yêu cầu. pattern="[0-9]{10}" yêu cầu dữ liệu là 10 chữ số, mỗi chữ số từ 0->9

<!-- Trường hợp 5 -->
<input type="password" minlength="8" value="123">  <!-- User gõ "123" -->
Trình duyệt sẽ chặn lại và thông báo dữ liệu quá ngắn do thuộc tính minlength="8" yêu cầu chuỗi nhập vào phải có ít nhất 8 ký tự. Giá trị "123" chỉ có 3 ký tự, không đủ độ dài tối thiểu được thiết lập.

A3: 
1. <label for="email"> quan trọng cho người dùng screen reader vì thẻ label này sẽ cho người dùng biết đây là 1 ô trống để nhập email đúng như cái tên của nó label cho email
2. <fieldset> và <legend> dùng đẻ nhóm các thẻ input có liên quan chặt chẽ với nhau về mặt logic, giúp người dùng dễ hình dung ra cấu trúc form
- <fieldset>: tạo 1 khung bao quanh nhóm các input
- <legend>: cung cấp tiêu đề cho cái khung đó
Ví dụ cụ thể
<fieldset>
    <legend>Thông tin vận chuyển</legend>
    <label for="name">Họ và tên:</label>
    <input type="text" id="name">
    <br>
    <label for="address">Địa chỉ:</label>
    <input type="text" id="address">
  </fieldset>

3. aria-label dùng khi muốn cung cấp nhãn cho screen reader nhưng không muốn hiển thị văn bản. không nên dùng khi đã có label vì nếu bạn dùng cả hai, aria-label thường sẽ "chiếm quyền" và khiến Screen Reader bỏ qua nội dung trong thẻ <label>. Điều này có thể gây nhầm lẫn nếu nội dung hai bên không khớp nhau hoàn toàn.

A4: 
1. Bình thường, trình duyệt sẽ tải tất cả hình ảnh trên trang web ngay khi bạn vừa truy cập. loading="lazy" (Lazy Loading) ra lệnh cho trình duyệt: "Chỉ tải ảnh này khi người dùng cuộn trang đến gần nó."
Nó cải thiện: 
Tốc độ tải trang (LCP): Giảm dung lượng dữ liệu cần tải ban đầu, giúp trang hiện ra nhanh hơn.

Tiết kiệm băng thông: Cực kỳ hữu ích cho người dùng dùng mạng 3G/4G, vì họ không phải trả tiền cho những bức ảnh họ chưa xem tới.

Hiệu suất thiết bị: Giảm tải cho bộ nhớ (RAM) và CPU của điện thoại.

Khi nào KHÔNG nên dùng?
Ảnh ở "Above the fold" (Vùng đầu trang): Những ảnh đập vào mắt người dùng ngay khi vừa mở trang (như Logo, Banner chính, ảnh đại diện bài viết) không được dùng lazy load. Nếu dùng, người dùng sẽ thấy một khoảng trắng trong tích tắc trước khi ảnh hiện ra, gây cảm giác trang bị chậm.

Đây là những kỹ thuật quan trọng giúp tối ưu hóa hiệu suất và khả năng tiếp cận (Accessibility) cho trang web của bạn:

1. Thuộc tính loading="lazy" trên thẻ <img>
Nó là gì?
Bình thường, trình duyệt sẽ tải tất cả hình ảnh trên trang web ngay khi bạn vừa truy cập. loading="lazy" (Lazy Loading) ra lệnh cho trình duyệt: "Chỉ tải ảnh này khi người dùng cuộn trang đến gần nó."

Cải thiện điều gì?

Tốc độ tải trang (LCP): Giảm dung lượng dữ liệu cần tải ban đầu, giúp trang hiện ra nhanh hơn.

Tiết kiệm băng thông: Cực kỳ hữu ích cho người dùng dùng mạng 3G/4G, vì họ không phải trả tiền cho những bức ảnh họ chưa xem tới.

Hiệu suất thiết bị: Giảm tải cho bộ nhớ (RAM) và CPU của điện thoại.

Khi nào KHÔNG nên dùng?

Ảnh ở "Above the fold" (Vùng đầu trang): Những ảnh đập vào mắt người dùng ngay khi vừa mở trang (như Logo, Banner chính, ảnh đại diện bài viết) không được dùng lazy load. Nếu dùng, người dùng sẽ thấy một khoảng trắng trong tích tắc trước khi ảnh hiện ra, gây cảm giác trang bị chậm.

2. Thẻ <video> và các định dạng
Tại sao nên cung cấp nhiều <source>?
Không phải trình duyệt nào cũng đọc được tất cả các loại file video. Khi bạn cung cấp nhiều <source>, trình duyệt sẽ quét từ trên xuống dưới và chọn định dạng đầu tiên mà nó hỗ trợ. Nếu bạn chỉ để 1 file mà trình duyệt không hỗ trợ, video sẽ không thể phát.

3 Format video web phổ biến:
MP4 (H.264): "Ông vua" phổ biến, chạy được trên gần như 100% trình duyệt và thiết bị.

WebM (VP9/AV1): Do Google phát triển, dung lượng nhẹ hơn MP4 nhưng chất lượng tương đương, hỗ trợ cực tốt trên Chrome và Firefox.

Ogg (Theora): Một định dạng mã nguồn mở, hiện nay ít dùng hơn hai loại trên nhưng vẫn được hỗ trợ bởi các trình duyệt cũ.

Đây là những kỹ thuật quan trọng giúp tối ưu hóa hiệu suất và khả năng tiếp cận (Accessibility) cho trang web của bạn:

1. Thuộc tính loading="lazy" trên thẻ <img>
Nó là gì?
Bình thường, trình duyệt sẽ tải tất cả hình ảnh trên trang web ngay khi bạn vừa truy cập. loading="lazy" (Lazy Loading) ra lệnh cho trình duyệt: "Chỉ tải ảnh này khi người dùng cuộn trang đến gần nó."

Cải thiện điều gì?

Tốc độ tải trang (LCP): Giảm dung lượng dữ liệu cần tải ban đầu, giúp trang hiện ra nhanh hơn.

Tiết kiệm băng thông: Cực kỳ hữu ích cho người dùng dùng mạng 3G/4G, vì họ không phải trả tiền cho những bức ảnh họ chưa xem tới.

Hiệu suất thiết bị: Giảm tải cho bộ nhớ (RAM) và CPU của điện thoại.

Khi nào KHÔNG nên dùng?

Ảnh ở "Above the fold" (Vùng đầu trang): Những ảnh đập vào mắt người dùng ngay khi vừa mở trang (như Logo, Banner chính, ảnh đại diện bài viết) không được dùng lazy load. Nếu dùng, người dùng sẽ thấy một khoảng trắng trong tích tắc trước khi ảnh hiện ra, gây cảm giác trang bị chậm.

2. Thẻ <video> và các định dạng
Tại sao nên cung cấp nhiều <source>?
Không phải trình duyệt nào cũng đọc được tất cả các loại file video. Khi bạn cung cấp nhiều <source>, trình duyệt sẽ quét từ trên xuống dưới và chọn định dạng đầu tiên mà nó hỗ trợ. Nếu bạn chỉ để 1 file mà trình duyệt không hỗ trợ, video sẽ không thể phát.

3 Format video web phổ biến:

MP4 (H.264): "Ông vua" phổ biến, chạy được trên gần như 100% trình duyệt và thiết bị.

WebM (VP9/AV1): Do Google phát triển, dung lượng nhẹ hơn MP4 nhưng chất lượng tương đương, hỗ trợ cực tốt trên Chrome và Firefox.

Ogg (Theora): Một định dạng mã nguồn mở, hiện nay ít dùng hơn hai loại trên nhưng vẫn được hỗ trợ bởi các trình duyệt cũ.

3. Thuộc tính alt (Alternative Text)
Dùng để làm gì?

Hỗ trợ người khiếm thị: Screen Reader sẽ đọc đoạn văn bản này lên.

Hiển thị khi lỗi: Nếu mạng yếu hoặc link ảnh chết, nội dung trong alt sẽ hiện ra để người dùng vẫn hiểu đó là ảnh gì.

Tốt cho SEO: Giúp Google hiểu nội dung bức ảnh để xếp hạng trên Google Images.

Ảnh iPhone 16:	alt="Điện thoại iPhone 16 màu xanh Teal mờ, góc nhìn nghiêng từ phía sau"	Cần miêu tả cụ thể sản phẩm và đặc điểm nhận dạng (màu sắc, góc chụp).
Ảnh trang trí:	alt="" (để trống)	Với ảnh chỉ để cho đẹp (như họa tiết nền, đường kẻ), hãy để alt trống để Screen Reader tự động bỏ qua, tránh làm phiền người dùng.
Biểu đồ doanh thu Q1/2026:	alt="Biểu đồ cột cho thấy doanh thu Q1/2026 đạt 5 tỷ VNĐ, tăng 15% so với cùng kỳ năm trước"	Không nên viết "Ảnh biểu đồ". Hãy tóm tắt nội dung/kết luận quan trọng nhất mà biểu đồ đó muốn truyền đạt.

A5: 1. Cách 1: <img> đơn thuần
Sử dụng khi bức ảnh chỉ là một thành phần minh họa đi kèm, nằm trong mạch nội dung của đoạn văn hoặc giao diện. Nếu xóa bức ảnh này đi, ý nghĩa của trang web có thể giảm đi nhưng cấu trúc thông tin không bị phá vỡ.

Đặc điểm: Không có chú thích hiển thị bên dưới, thường dùng cho các mục nhỏ, danh sách hoặc icon.

Ví dụ thực tế:

Thumbnail trong danh sách tìm kiếm: Khi bạn tìm kiếm "iPhone", một danh sách hiện ra với hàng chục ảnh nhỏ. Ở đây ảnh chỉ cần alt để nhận diện, không cần chú thích riêng biệt vì tên và giá đã nằm ở các thẻ <h3> hay <p> bên cạnh.

Avatar người dùng: Trong phần bình luận sản phẩm, ảnh đại diện của khách hàng chỉ cần thẻ img. Chú thích cho ảnh là không cần thiết và gây nhiễu giao diện.

2. Cách 2: <figure> + <figcaption>
Sử dụng khi bức ảnh là một nội dung độc lập (self-contained). "Độc lập" ở đây nghĩa là bạn có thể di chuyển cả khối <figure> này sang một vị trí khác (ví dụ từ giữa trang xuống cuối trang) mà không làm mất đi ý nghĩa của nó hoặc của bài viết.

Đặc điểm: Cung cấp một chú thích rõ ràng cho bức ảnh. Screen Reader sẽ đọc mối liên kết giữa chú thích (figcaption) và hình ảnh này, giúp người dùng hiểu sâu hơn về bối cảnh.

Ví dụ thực tế:

Ảnh chi tiết trong bài viết đánh giá (Review): Trong bài "Đánh giá camera iPhone 16", bạn chèn một bức ảnh chụp đêm. Bạn dùng <figure> để bao quanh ảnh đó và <figcaption> để ghi "Ảnh chụp phơi sáng 3 giây bằng chế độ Night Mode trên iPhone 16".

Sơ đồ/Biểu đồ trong trang báo cáo: Một biểu đồ tăng trưởng doanh số cần có chú thích bên dưới để giải thích các thông số. Sử dụng <figure> giúp tách biệt biểu đồ này ra khỏi các đoạn văn phân tích xung quanh.