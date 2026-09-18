# Chế độ hiện đại, "use strict"

Trong một thời gian dài, JavaScript đã phát triển mà không gặp vấn đề về tính tương thích. Các tính năng mới được thêm vào ngôn ngữ trong khi các chức năng cũ không thay đổi.

Điều đó có lợi thế là không bao giờ phá vỡ (*breaking*) các code hiện có. Nhưng nhược điểm là bất kỳ sai lầm hoặc quyết định chưa hoàn hảo nào của những người tạo ra JavaScript đều bị mắc kẹt lại trong ngôn ngữ này mãi mãi.

Trường hợp này kéo dài cho đến năm 2009 khi ECMAScript 5 (ES5) xuất hiện. Nó đã thêm các tính năng mới vào ngôn ngữ và sửa đổi một số tính năng hiện có. Để giữ cho các code cũ tiếp tục hoạt động, hầu hết các sửa đổi như vậy đều bị tắt (*off*) theo mặc định. Bạn cần phải kích hoạt (*enable*) chúng một cách rõ ràng bằng một chỉ thị (*directive*) đặc biệt: `"use strict"`.

## “use strict”

*Directive* này trông giống như một chuỗi (*string*): `"use strict"` hoặc `'use strict'`. Khi nó được đặt ở đầu một *script*, toàn bộ *script* đó sẽ hoạt động theo cách "hiện đại" (*modern*).

Ví dụ:

```javascript
"use strict";

// this code works the modern way
...
```

Khá sớm thôi chúng ta sẽ học về hàm (*functions* - một cách để nhóm các lệnh), vì vậy hãy lưu ý trước rằng `"use strict"` có thể được đặt ở đầu một hàm. Việc làm đó sẽ kích hoạt *strict mode* (chế độ nghiêm ngặt) chỉ trong hàm đó. Nhưng thông thường mọi người sử dụng nó cho toàn bộ *script*.

## Đảm bảo rằng “use strict” nằm ở trên cùng

Vui lòng đảm bảo rằng `"use strict"` nằm ở trên cùng của các *scripts* của bạn, nếu không *strict mode* có thể sẽ không được kích hoạt.

*Strict mode* không được kích hoạt ở đây:

```javascript
alert("some code");
// "use strict" below is ignored--it must be at the top

"use strict";
// strict mode is not activated
```

Chỉ các chú thích (*comments*) mới có thể xuất hiện phía trên `"use strict"`.

## Không có cách nào để hủy bỏ use strict

Không có *directive* nào như `"no use strict"` để đưa *engine* trở lại hành vi cũ.

Một khi chúng ta bước vào *strict mode*, sẽ không có cách nào quay lại.

## Browser console (Bảng điều khiển của trình duyệt)

Khi bạn sử dụng bảng điều khiển dành cho nhà phát triển (*developer console*) để chạy code, xin lưu ý rằng nó không sử dụng `use strict` theo mặc định.

Đôi khi, khi `use strict` tạo ra sự khác biệt, bạn sẽ nhận được kết quả không chính xác.

Vậy, làm thế nào để thực sự sử dụng `use strict` trong *console*?

Đầu tiên, bạn có thể thử nhấn `Shift+Enter` để nhập nhiều dòng và đặt `use strict` ở trên cùng, như thế này:

```javascript
'use strict'; <Shift+Enter for a newline>
//  ...your code
<Enter to run>
```

Nó hoạt động trong hầu hết các trình duyệt, cụ thể là Firefox và Chrome.

Nếu nó không hoạt động, ví dụ như trong một trình duyệt cũ, có một cách hơi "xấu" nhưng đáng tin cậy để đảm bảo `use strict` hoạt động. Đặt nó bên trong một *wrapper* (vỏ bọc) như thế này:

```javascript
(function() {
  'use strict';

  // ...your code here...
})()
```

## Chúng ta có nên “use strict”?

Câu hỏi này nghe có vẻ hiển nhiên, nhưng không phải vậy.

Có người có thể khuyên nên bắt đầu các *scripts* bằng `"use strict"`… Nhưng bạn biết điều gì tuyệt vời không?

JavaScript hiện đại hỗ trợ các *classes* (lớp) và *modules* (mô-đun) - những cấu trúc ngôn ngữ nâng cao (chắc chắn chúng ta sẽ học đến chúng), cho phép tự động kích hoạt `use strict`. Do đó, chúng ta không cần thêm *directive* `"use strict"` nếu chúng ta sử dụng chúng.

Vì vậy, ở thời điểm hiện tại, `"use strict";` là một vị khách được chào đón ở phần trên cùng của các *scripts*. Sau này, khi code của bạn hoàn toàn nằm trong các *classes* và *modules*, bạn có thể bỏ qua nó.

Cho đến lúc này, chúng ta đã được biết về `use strict` một cách tổng quan.

Trong các chương tiếp theo, khi chúng ta học về các tính năng của ngôn ngữ, chúng ta sẽ thấy sự khác biệt giữa *strict mode* và *old mode* (chế độ cũ). May mắn thay, không có quá nhiều sự khác biệt và chúng thực sự làm cho việc lập trình của chúng ta trở nên tốt hơn.

Tất cả các ví dụ trong *tutorial* này đều giả định rằng *strict mode* đang được sử dụng, trừ khi (rất hiếm khi) được chỉ định khác đi.