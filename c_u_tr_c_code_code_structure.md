# Cấu trúc code

Điều đầu tiên chúng ta sẽ học là các khối xây dựng của code.

## Statements (Các câu lệnh)

Các *statements* là các cấu trúc cú pháp (*syntax constructs*) và các lệnh (*commands*) thực hiện các hành động.

Chúng ta đã thấy một *statement*, `alert('Hello, world!')`, dùng để hiển thị thông báo "Hello, world!".

Chúng ta có thể có bao nhiêu *statements* trong code của mình tùy thích. Các *statements* có thể được phân tách bằng dấu chấm phẩy (*semicolon*).

Ví dụ, ở đây chúng ta chia thông báo "Hello World" thành hai lệnh `alert`:

```javascript
alert('Hello'); alert('World');
```

Thông thường, các *statements* được viết trên các dòng riêng biệt để code dễ đọc hơn:

```javascript
alert('Hello');
alert('World');
```

## Semicolons (Dấu chấm phẩy)

Dấu chấm phẩy có thể được bỏ qua trong hầu hết các trường hợp khi có dấu ngắt dòng (*line break*).

Đoạn code này cũng sẽ hoạt động:

```javascript
alert('Hello')
alert('World')
```

Ở đây, JavaScript hiểu dấu ngắt dòng là một dấu chấm phẩy ngầm định (*implicit semicolon*). Điều này được gọi là tự động chèn dấu chấm phẩy (*automatic semicolon insertion*).

Trong hầu hết các trường hợp, một dòng mới ngụ ý một dấu chấm phẩy. Nhưng "trong hầu hết các trường hợp" không có nghĩa là "luôn luôn"!

Có những trường hợp một dòng mới không có nghĩa là một dấu chấm phẩy. Ví dụ:

```javascript
alert(3 +
1
+ 2);
```

Code sẽ xuất ra `6` bởi vì JavaScript không chèn dấu chấm phẩy ở đây. Rõ ràng theo trực giác, nếu dòng kết thúc bằng dấu cộng `+`, thì đó là một "biểu thức chưa hoàn chỉnh" (*incomplete expression*), vì vậy đặt một dấu chấm phẩy ở đó sẽ không chính xác. Và trong trường hợp này, nó hoạt động đúng như mong đợi.

Nhưng có những tình huống JavaScript "thất bại" trong việc giả định một dấu chấm phẩy ở nơi nó thực sự cần thiết.

Các lỗi (*errors*) xảy ra trong những trường hợp như vậy khá khó để tìm và sửa.

### An example of an error (Một ví dụ về lỗi)

Nếu bạn tò mò muốn xem một ví dụ cụ thể của lỗi như vậy, hãy xem thử đoạn code này:

```javascript
alert("Hello");

[1, 2].forEach(alert);
```

Chưa cần phải suy nghĩ về ý nghĩa của cặp ngoặc vuông `[]` và `forEach`. Chúng ta sẽ học chúng sau. Bây giờ, chỉ cần nhớ kết quả khi chạy code: nó sẽ hiển thị `Hello`, sau đó là `1`, rồi `2`.

Bây giờ hãy xóa dấu chấm phẩy sau lệnh `alert`:

```javascript
alert("Hello")

[1, 2].forEach(alert);
```

Sự khác biệt so với đoạn code trên chỉ là một ký tự: dấu chấm phẩy ở cuối dòng đầu tiên đã biến mất.

Nếu chúng ta chạy đoạn code này, chỉ có chữ `Hello` đầu tiên xuất hiện (và có một lỗi, bạn có thể cần mở *console* để xem nó). Sẽ không có số nào hiện ra nữa.

Đó là bởi vì JavaScript không giả định một dấu chấm phẩy trước cặp dấu ngoặc vuông `[...]`. Vì vậy, code trong ví dụ cuối cùng được coi là một *statement* duy nhất.

Đây là cách *engine* nhìn thấy nó:

```javascript
alert("Hello")[1, 2].forEach(alert);
```

Trông thật kỳ lạ phải không? Việc hợp nhất trong trường hợp này hoàn toàn sai. Chúng ta cần đặt một dấu chấm phẩy sau `alert` để code hoạt động chính xác.

Điều này cũng có thể xảy ra trong các tình huống khác.

Chúng tôi khuyến nghị nên đặt dấu chấm phẩy giữa các *statements* ngay cả khi chúng được phân tách bằng các dòng mới. Quy tắc này được cộng đồng áp dụng rộng rãi. Xin lưu ý một lần nữa – hầu hết các trường hợp bạn có thể bỏ dấu chấm phẩy. Nhưng việc sử dụng chúng sẽ an toàn hơn – đặc biệt là đối với người mới bắt đầu.

## Comments (Chú thích)

Theo thời gian, các chương trình trở nên ngày càng phức tạp. Sẽ là cần thiết khi thêm các *comments* để mô tả những gì code làm và tại sao nó lại làm như vậy.

Các *comments* có thể được đặt vào bất kỳ vị trí nào của một *script*. Chúng không ảnh hưởng đến việc thực thi vì *engine* đơn giản là bỏ qua chúng.

**Các *comments* trên một dòng (One-line comments)** bắt đầu bằng hai ký tự gạch chéo `//`.

Phần còn lại của dòng là một *comment*. Nó có thể chiếm một dòng riêng hoặc nằm ngay theo sau một *statement*.

Giống như ở đây:

```javascript
// This comment occupies a line of its own
alert('Hello');

alert('World'); // This comment follows the statement
```

**Các *comments* trên nhiều dòng (Multiline comments)** bắt đầu bằng một dấu gạch chéo và một dấu sao `/*` và kết thúc bằng một dấu sao và một dấu gạch chéo `*/`.

Giống như thế này:

```javascript
/* An example with two messages.
This is a multiline comment.
*/
alert('Hello');
alert('World');
```

Nội dung của các *comments* sẽ bị bỏ qua, vì vậy nếu chúng ta đặt code bên trong `/* … */`, nó sẽ không được thực thi.

Đôi khi có thể rất tiện lợi khi tạm thời vô hiệu hóa (*disable*) một phần code:

```javascript
/* Commenting out the code
alert('Hello');
*/
alert('World');
```

**Sử dụng phím tắt! (Use hotkeys!)**
Trong hầu hết các *editors*, một dòng code có thể được chuyển thành *comment* bằng cách nhấn phím tắt `Ctrl+/` cho *comment* một dòng và `Ctrl+Shift+/` (hoặc tương tự) cho các *comments* nhiều dòng (chọn một đoạn code và nhấn phím tắt). Đối với máy Mac, hãy thử dùng `Cmd` thay vì `Ctrl` và `Option` thay vì `Shift`.

**Không hỗ trợ chú thích lồng nhau! (Nested comments are not supported!)**
Không được để một cặp `/*...*/` này nằm bên trong một cặp `/*...*/` khác.
Đoạn code như vậy sẽ chết và báo lỗi:

```javascript
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```

Xin đừng ngần ngại viết *comment* cho code của bạn.

Các *comments* làm tăng kích thước (*footprint*) tổng thể của code, nhưng điều đó hoàn toàn không phải là vấn đề. Có rất nhiều công cụ giúp thu nhỏ (*minify*) code trước khi *publish* (xuất bản) lên một *production server* (máy chủ thật). Chúng xóa bỏ các *comments*, do đó những chú thích này sẽ không xuất hiện trong các *scripts* đang chạy. Vì vậy, các *comments* hoàn toàn không có tác động tiêu cực nào đối với *production*.

Sau này trong *tutorial*, sẽ có một chương là "Code quality" (Chất lượng code) cũng sẽ giải thích chi tiết hơn về cách viết các *comments* sao cho tốt.