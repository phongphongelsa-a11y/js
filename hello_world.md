# Hello, world!

Phần này của tutorial tập trung vào core JavaScript, tức là bản thân ngôn ngữ lập trình.

Nhưng chúng ta cần một môi trường làm việc (*working environment*) để chạy các *scripts* của mình và, vì cuốn sách này được xuất bản trực tuyến, trình duyệt (*browser*) là một lựa chọn tốt. Chúng tôi sẽ giữ số lượng các lệnh dành riêng cho trình duyệt (như `alert`) ở mức tối thiểu để bạn không mất thời gian vào chúng nếu bạn dự định tập trung vào một môi trường khác (như Node.js). Chúng tôi sẽ tập trung vào JavaScript trong trình duyệt ở phần tiếp theo của tutorial.

Vì vậy, trước tiên, hãy xem cách chúng ta đính kèm một *script* vào một trang web. Đối với các môi trường *server-side* (như Node.js), bạn có thể thực thi *script* bằng một lệnh như `"node my.js"`.

## Thẻ "script"

Các chương trình JavaScript có thể được chèn vào gần như bất kỳ đâu trong một tài liệu HTML (*HTML document*) bằng cách sử dụng thẻ `<script>`.

Ví dụ:

```html
<!DOCTYPE HTML>
<html>
<body>

  <p>Before the script...</p>

  <script>
    alert( 'Hello, world!' );
  </script>

  <p>...After the script.</p>

</body>
</html>
```

Bạn có thể chạy ví dụ này bằng cách nhấp vào nút "Play" ở góc trên bên phải của hộp code trên trang chủ.

Thẻ `<script>` chứa mã JavaScript và nó sẽ tự động được thực thi khi trình duyệt xử lý thẻ này.

## Modern markup (Markup hiện đại)

Thẻ `<script>` có một vài thuộc tính (*attributes*) hiếm khi được sử dụng ngày nay nhưng vẫn có thể được tìm thấy trong các đoạn code cũ:

**Thuộc tính `type`: `<script type=…>`**
Tiêu chuẩn HTML cũ, HTML4, yêu cầu một *script* phải có một `type`. Thường thì nó là `type="text/javascript"`. Điều này hiện không còn bắt buộc nữa. Ngoài ra, tiêu chuẩn HTML hiện đại đã thay đổi hoàn toàn ý nghĩa của thuộc tính này. Ngày nay, nó có thể được sử dụng cho các *JavaScript modules*. Nhưng đó là một chủ đề nâng cao, chúng ta sẽ nói về *modules* ở một phần khác của tutorial.

**Thuộc tính `language`: `<script language=…>`**
Thuộc tính này được dùng để thể hiện ngôn ngữ của *script*. Thuộc tính này không còn ý nghĩa nữa vì JavaScript hiện là ngôn ngữ mặc định. Bạn không cần phải sử dụng nó.

**Comments trước và sau các scripts**
Trong các cuốn sách và hướng dẫn thực sự cổ xưa, bạn có thể tìm thấy các comments (chú thích) bên trong các thẻ `<script>`, giống như thế này:

```html
<script type="text/javascript">
<!--
...
//-->
</script>
```

Thủ thuật này không còn được sử dụng trong JavaScript hiện đại. Các comments này giúp ẩn code JavaScript khỏi các trình duyệt cũ không biết cách xử lý thẻ `<script>`. Vì các trình duyệt được phát hành trong 15 năm qua không còn gặp vấn đề này nữa, nên loại comment này có thể giúp bạn nhận diện những đoạn code thực sự rất cũ.

## External scripts (Scripts bên ngoài)

Nếu chúng ta có nhiều code JavaScript, chúng ta có thể đặt nó vào một file riêng biệt.

Các files *script* được đính kèm vào HTML thông qua thuộc tính `src`:

```html
<script src="/path/to/script.js"></script>
```

Ở đây, `/path/to/script.js` là một đường dẫn tuyệt đối (*absolute path*) đến *script* từ *site root* (thư mục gốc của trang web). Người ta cũng có thể cung cấp một đường dẫn tương đối (*relative path*) từ trang hiện tại. Ví dụ, `src="script.js"`, cũng giống như `src="./script.js"`, sẽ có nghĩa là một file `"script.js"` nằm trong thư mục hiện tại.

Chúng ta cũng có thể cung cấp một URL đầy đủ. Ví dụ:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Để đính kèm nhiều *scripts*, hãy sử dụng nhiều thẻ:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

**Lưu ý:**
Theo quy tắc, chỉ những *scripts* đơn giản nhất mới được đặt trực tiếp vào HTML. Những *scripts* phức tạp hơn nên được đặt trong các files riêng biệt.

Lợi ích của một file riêng biệt là trình duyệt sẽ tải nó xuống và lưu trữ nó trong *cache* (bộ nhớ đệm) của nó.
Các trang khác tham chiếu đến cùng một *script* sẽ lấy nó từ *cache* thay vì phải tải xuống lại, do đó file thực sự chỉ được tải xuống một lần.
Điều đó làm giảm lưu lượng mạng (*traffic*) và làm cho các trang tải nhanh hơn.

**Nếu `src` được thiết lập, nội dung bên trong thẻ sẽ bị bỏ qua.**
Một thẻ `<script>` đơn lẻ không thể có cả thuộc tính `src` lẫn code ở bên trong.
Điều này sẽ không hoạt động:

```html
<script src="file.js">
  alert(1); // the content is ignored, because src is set
</script>
```

Chúng ta phải chọn giữa việc sử dụng `<script src="…">` bên ngoài hoặc một thẻ `<script>` thông thường chứa code.

Ví dụ trên có thể được tách thành hai *scripts* riêng biệt để hoạt động:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```

## Tóm tắt

Chúng ta có thể sử dụng thẻ `<script>` để thêm code JavaScript vào một trang web. 
Các thuộc tính `type` và `language` là không bắt buộc. 
Một *script* trong một file bên ngoài có thể được chèn bằng cách sử dụng `<script src="path/to/script.js"></script>`.

Còn rất nhiều điều để học về các *scripts* trong trình duyệt và sự tương tác của chúng với trang web. Nhưng hãy nhớ rằng phần này của tutorial được dành riêng cho ngôn ngữ JavaScript, vì vậy chúng ta không nên làm bản thân bị phân tâm bởi các implementations dành riêng cho trình duyệt. Chúng ta sẽ sử dụng trình duyệt như một cách để chạy JavaScript, điều này rất thuận tiện cho việc đọc trực tuyến, nhưng đó chỉ là một trong nhiều cách.

---

## Tasks (Bài tập)

### Show an alert (Hiển thị một thông báo)
Độ quan trọng: 5

Tạo một trang hiển thị thông báo "I'm JavaScript!".

Bạn có thể làm điều đó trong một *sandbox*, hoặc trên ổ cứng của bạn, điều đó không quan trọng, chỉ cần đảm bảo rằng nó hoạt động.

**Solution (Lời giải)**

```html
<!DOCTYPE html>
<html>
<body>
  <script>
    alert( "I'm JavaScript!" );
  </script>
</body>
</html>
```

### Show an alert with an external script (Hiển thị một thông báo với external script)
Độ quan trọng: 5

Lấy lời giải của bài tập trước "Show an alert". Sửa đổi nó bằng cách trích xuất nội dung *script* ra một file bên ngoài tên là `alert.js`, nằm trong cùng thư mục.

Mở trang đó ra và đảm bảo rằng `alert` vẫn hoạt động.

**Solution (Lời giải)**

Mã HTML:

```html
<!DOCTYPE html>
<html>
<body>
  <script src="alert.js"></script>
</body>
</html>
```

Đối với file `alert.js` trong cùng thư mục:

```javascript
alert( "I'm JavaScript!" );
```