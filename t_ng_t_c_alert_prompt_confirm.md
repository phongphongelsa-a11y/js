# Tương tác: alert, prompt, confirm

Vì chúng ta sẽ sử dụng trình duyệt làm môi trường demo cho mình, hãy cùng xem qua một vài hàm để tương tác với người dùng: `alert`, `prompt` và `confirm`.

## alert

Hàm này chúng ta đã thấy rồi. Nó hiển thị một thông báo và chờ người dùng nhấn nút “OK”.

Ví dụ:

```javascript
alert("Hello");
```

Cửa sổ nhỏ chứa thông báo được gọi là một *modal window* (cửa sổ modal). Từ “modal” có nghĩa là khách truy cập không thể tương tác với phần còn lại của trang, không thể nhấn các nút khác, v.v., cho đến khi họ giải quyết xong cửa sổ đó. Trong trường hợp này – là cho đến khi họ nhấn “OK”.

## prompt

Hàm `prompt` nhận vào hai đối số (*arguments*):

```javascript
result = prompt(title, [default]);
```

Nó hiển thị một *modal window* với một thông báo dạng văn bản, một trường nhập liệu (*input field*) dành cho khách truy cập, và các nút OK/Cancel.

`title`
Văn bản hiển thị cho khách truy cập.

`default`
Một tham số thứ hai tùy chọn, là giá trị khởi tạo (*initial value*) cho trường nhập liệu.

**Cặp dấu ngoặc vuông trong cú pháp `[...]`**
Cặp dấu ngoặc vuông bao quanh `default` trong cú pháp ở trên biểu thị rằng tham số này là tùy chọn (*optional*), không bắt buộc.

Khách truy cập có thể gõ một thứ gì đó vào trường nhập liệu của *prompt* và nhấn OK. Khi đó, chúng ta sẽ nhận được văn bản đó trong `result`. Hoặc họ có thể hủy việc nhập liệu bằng cách nhấn nút Cancel hoặc nhấn phím Esc, khi đó chúng ta sẽ nhận được `null` làm `result`.

Lời gọi đến `prompt` sẽ trả về văn bản từ trường nhập liệu hoặc `null` nếu việc nhập liệu bị hủy bỏ.

Ví dụ:

```javascript
let age = prompt('How old are you?', 100);

alert(`You are ${age} years old!`); // You are 100 years old!
```

**Trong IE: luôn cung cấp một giá trị default**
Tham số thứ hai là tùy chọn, nhưng nếu chúng ta không cung cấp nó, Internet Explorer sẽ chèn văn bản `"undefined"` vào trong *prompt*.
Hãy chạy đoạn code này trong Internet Explorer để thấy:

```javascript
let test = prompt("Test");
```

Vì vậy, để các *prompts* trông tử tế trong IE, chúng tôi khuyên bạn luôn luôn cung cấp đối số thứ hai:

```javascript
let test = prompt("Test", ''); // <-- dành cho IE
```

## confirm

Cú pháp:

```javascript
result = confirm(question);
```

Hàm `confirm` hiển thị một *modal window* với một câu hỏi (`question`) và hai nút: OK và Cancel.

Kết quả trả về là `true` nếu nút OK được nhấn và `false` nếu ngược lại.

Ví dụ:

```javascript
let isBoss = confirm("Are you the boss?");

alert( isBoss ); // true nếu OK được nhấn
```

## Tóm tắt

Chúng ta đã tìm hiểu 3 hàm dành riêng cho trình duyệt để tương tác với khách truy cập:

* `alert`
  Hiển thị một thông báo.
* `prompt`
  Hiển thị một thông báo yêu cầu người dùng nhập văn bản. Nó trả về văn bản đó hoặc, nếu nút Cancel hay phím Esc được nhấn, trả về `null`.
* `confirm`
  Hiển thị một thông báo và chờ người dùng nhấn “OK” hoặc “Cancel”. Nó trả về `true` cho OK và `false` cho Cancel/Esc.

Tất cả các phương thức này đều là *modal*: chúng tạm dừng việc thực thi *script* và không cho phép khách truy cập tương tác với phần còn lại của trang web cho đến khi cửa sổ bị tắt.

Có hai hạn chế chung cho tất cả các phương thức ở trên:

1. Vị trí chính xác của *modal window* được quyết định bởi trình duyệt. Thông thường, nó nằm ở vị trí trung tâm.
2. Giao diện chính xác của cửa sổ cũng phụ thuộc vào trình duyệt. Chúng ta không thể sửa đổi nó.

Đó là cái giá của sự đơn giản. Có những cách khác để hiển thị các cửa sổ đẹp hơn và có khả năng tương tác phong phú hơn với khách truy cập, nhưng nếu "những thứ phụ trợ hoa mỹ" (*bells and whistles*) không quá quan trọng, thì các phương thức này hoạt động rất tốt.

---

## Bài tập (Tasks)

### Một trang web đơn giản (A simple page)

Độ quan trọng: 4

Hãy tạo một trang web yêu cầu nhập một tên và xuất nó ra.

**Lời giải (Solution)**

Mã JavaScript:

```javascript
let name = prompt("What is your name?", "");
alert(name);
```

Toàn bộ trang web:

```html
<!DOCTYPE html>
<html>
<body>

  <script>
    'use strict';

    let name = prompt("What is your name?", "");
    alert(name);
  </script>

</body>
</html>
```