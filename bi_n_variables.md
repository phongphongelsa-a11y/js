# Biến (Variables)

Hầu hết thời gian, một ứng dụng JavaScript cần làm việc với thông tin. Dưới đây là hai ví dụ:

1. Một cửa hàng trực tuyến (Online shop) – thông tin có thể bao gồm hàng hóa đang được bán và giỏ hàng (*shopping cart*).
2. Một ứng dụng trò chuyện (Chat application) – thông tin có thể bao gồm người dùng (*users*), tin nhắn (*messages*), v.v.

Các *variables* (biến) được sử dụng để lưu trữ những thông tin này.

## Một variable (A variable)

Một *variable* là một "kho lưu trữ có tên" (*named storage*) dành cho dữ liệu. Chúng ta có thể sử dụng các *variables* để lưu trữ thông tin về hàng hóa, khách truy cập và những thứ khác.

Để tạo ra một *variable* trong JavaScript, hãy sử dụng *keyword* (từ khóa) `let`.

Câu lệnh dưới đây tạo ra (nói cách khác: khai báo - *declares*) một *variable* với tên gọi là "message":

```javascript
let message;
```

Bây giờ, chúng ta có thể gán (*assign*) một số dữ liệu cho nó bằng cách sử dụng toán tử gán (*assignment operator*) `=`:

```javascript
let message;

message = 'Hello'; // lưu trữ chuỗi (string)
```

Chuỗi (*string*) này hiện đã được lưu vào vùng nhớ liên kết với *variable* đó. Chúng ta có thể truy cập nó bằng cách sử dụng tên của *variable*:

```javascript
let message;
message = 'Hello!';

alert(message); // hiển thị nội dung của variable
```

Để ngắn gọn hơn, chúng ta có thể kết hợp việc khai báo (*variable declaration*) và gán giá trị (*assignment*) vào cùng một dòng:

```javascript
let message = 'Hello!'; // khai báo variable và gán giá trị

alert(message); // Hello!
```

Chúng ta cũng có thể khai báo nhiều *variables* trên một dòng:

```javascript
let user = 'John', age = 25, message = 'Hello';
```

Điều này có vẻ ngắn gọn hơn, nhưng chúng tôi không khuyến khích làm vậy. Vì lợi ích của việc dễ đọc (*readability*), hãy sử dụng một dòng riêng biệt cho mỗi *variable*:

```javascript
let user = 'John';
let age = 25;
let message = 'Hello';
```

Một số người cũng định dạng (*format*) việc khai báo nhiều *variables* theo kiểu nhiều dòng (*multiline*) như thế này:

```javascript
let user = 'John',
  age = 25,
  message = 'Hello';
```

...Hoặc thậm chí theo kiểu dấu phẩy đặt trước (*comma-first*):

```javascript
let user = 'John'
  , age = 25
  , message = 'Hello';
```

Về mặt kỹ thuật, tất cả các biến thể này đều thực hiện cùng một chức năng. Vì vậy, đây chỉ là vấn đề về sở thích cá nhân và tính thẩm mỹ.

**Từ khóa `var` (The `var` keyword)**
Trong các *scripts* cũ hơn, bạn cũng có thể tìm thấy một *keyword* khác là `var` thay vì `let`:
```javascript
var message = 'Hello';
```
Từ khóa `var` gần giống với `let`. Nó cũng khai báo một *variable*, nhưng theo một cách hơi khác biệt, mang tính "cổ điển" (*old-school*) hơn. 
Có một số khác biệt tinh tế giữa `let` và `var`, nhưng chúng chưa thực sự quan trọng đối với chúng ta ở thời điểm hiện tại. Chúng ta sẽ tìm hiểu chi tiết về chúng trong chương "The old 'var'".

## Một sự so sánh trong đời thực (A real-life analogy)

Chúng ta có thể dễ dàng nắm bắt khái niệm về *variable* nếu hình dung nó như một "chiếc hộp" chứa dữ liệu, với một nhãn dán duy nhất ghi tên của nó.

Ví dụ, *variable* `message` có thể được tưởng tượng là một chiếc hộp được dán nhãn `"message"` và có chứa giá trị `"Hello!"` bên trong.

Chúng ta có thể đưa bất kỳ giá trị nào vào chiếc hộp đó.

Chúng ta cũng có thể thay đổi nó bao nhiêu lần tùy thích:

```javascript
let message;

message = 'Hello!';

message = 'World!'; // giá trị bị thay đổi

alert(message);
```

Khi giá trị bị thay đổi, dữ liệu cũ sẽ bị xóa khỏi *variable*:

Chúng ta cũng có thể khai báo hai *variables* và sao chép (*copy*) dữ liệu từ *variable* này sang *variable* khác.

```javascript
let Hello = 'Hello world!';

let message;

// copy giá trị của 'Hello' sang 'message'
message = Hello;

// bây giờ cả hai variables đều chứa cùng một data
alert(Hello); // Hello world!
alert(message); // Hello world!
```

**Khai báo hai lần sẽ gây ra lỗi (Declaring twice triggers an error)**
Một *variable* chỉ nên được khai báo một lần duy nhất.
Việc khai báo lại cùng một *variable* sẽ dẫn đến một *error* (lỗi):
```javascript
let message = "This";

// lặp lại keyword 'let' sẽ dẫn đến lỗi
let message = "That"; // SyntaxError: 'message' has already been declared
```
Vì vậy, chúng ta chỉ nên khai báo (*declare*) một *variable* một lần duy nhất và sau đó tham chiếu đến nó (refers to it) mà không cần sử dụng lại `let`.

**Các ngôn ngữ lập trình hàm (Functional languages)**
Điều thú vị là có những ngôn ngữ lập trình hàm (*functional programming languages*) như Scala hoặc Erlang hoàn toàn không cho phép thay đổi các *variables* đã gán.
Trong các ngôn ngữ đó, "chiếc hộp" giống như được niêm phong vĩnh viễn. Nếu chúng ta muốn lưu trữ thứ gì đó khác, chúng ta phải tạo một chiếc hộp mới (tức là khai báo một *variable* mới). Chúng ta không thể tái sử dụng chiếc hộp cũ.
Mặc dù điều này có vẻ kỳ lạ lúc đầu, nhưng những ngôn ngữ này hoàn toàn có khả năng phát triển các công việc nghiêm túc. Hơn thế nữa, các kiến trúc như vậy rất phù hợp cho các tính toán song song (*parallel computations*).

## Đặt tên biến (Variable naming)

Chỉ có hai hạn chế về tên của *variable* trong JavaScript:
1. Tên chỉ được chứa các chữ cái, chữ số (*digits*), hoặc các ký hiệu `$` và `_`.
2. Ký tự đầu tiên không được phép là một chữ số.

Ví dụ về những tên hợp lệ:

```javascript
let userName;
let test123;
```

Khi tên chứa nhiều từ, cách viết *camelCase* thường được sử dụng. Cụ thể là, các từ đi sau nhau, mỗi từ đều bắt đầu bằng chữ cái viết hoa: `myVeryLongName`.

Điều thú vị là, ký hiệu đô la `$` và dấu gạch dưới `_` cũng có thể được sử dụng trong tên *variable*. Chúng là những ký hiệu thông thường, giống như các chữ cái, không mang bất kỳ ý nghĩa đặc biệt nào.

Các tên sau đều hợp lệ:

```javascript
let $ = 1; // khai báo một variable mang tên "$"
let _ = 2; // và bây giờ là một variable mang tên "_"

alert($ + _); // 3
```

Ví dụ về các tên *variable* không hợp lệ (*invalid*):

```javascript
let 1a; // không thể bắt đầu bằng chữ số

let my-name; // dấu gạch ngang '-' không được cho phép trong tên variable
```

**Phân biệt chữ hoa chữ thường (Case matters)**
Các *variables* có tên `apple` và `APPLE` là hai *variables* hoàn toàn khác nhau.

**Các ký tự không phải Latinh (Non-Latin letters) được cho phép, nhưng không được khuyến khích**
Có thể sử dụng bất kỳ ngôn ngữ nào, kể cả các chữ cái Cyrillic hoặc thậm chí là chữ tượng hình (*hieroglyphs*), chẳng hạn như:
```javascript
let имя = '...';
let 我 = '...';
```
Về mặt kỹ thuật, không có lỗi (*error*) nào xảy ra ở đây. Những cái tên như vậy vẫn được cho phép. Tuy nhiên, có một quy ước quốc tế (international convention) là chỉ sử dụng tiếng Anh trong tên *variables*. Ngay cả khi chúng ta viết một *script* nhỏ cho riêng mình, nó vẫn có thể có một tuổi thọ dài lâu sau này. Bất kỳ ai từ các quốc gia khác cũng có thể cần phải đọc nó sau một thời gian.

## Từ khóa dự trữ (Reserved words)

Có một danh sách các *reserved words* (từ khóa dự trữ / từ dành riêng), những từ này không thể được sử dụng làm tên của *variable* vì bản thân ngôn ngữ đã sử dụng chúng.

Ví dụ: `let`, `class`, `return`, và `function` đều bị dự trữ.

Đoạn code dưới đây sẽ sinh ra lỗi cú pháp (*SyntaxError*):

```javascript
let let = 5; // không thể đặt tên variable là "let", lỗi!
let return = 5; // cũng không thể gọi nó là "return", lỗi!
```

**Gán giá trị mà không sử dụng `use strict` (An assignment without `use strict`)**
Thông thường, chúng ta cần xác định một *variable* trước khi sử dụng nó. Tuy nhiên, trong thời gian đầu, về mặt kỹ thuật, việc gán giá trị cho một *variable* có thể thực hiện được mà không cần dùng `let`. *Variable* đó sẽ được tạo tự động nếu `use strict` không được đặt. Tuy nhiên, đây là một thực tiễn tệ (*bad practice*) và sẽ gây ra lỗi nếu chúng ta bật *strict mode*:

```javascript
"use strict";

num = 5; // error: num is not defined
```

## Hằng số (Constants)

Để khai báo một *variable* có giá trị không bao giờ thay đổi, hãy sử dụng `const` thay vì `let`:

```javascript
const myBirthday = '18.04.1982';
```

Các *variables* được khai báo bằng `const` được gọi là các hằng số (*constants*). Chúng không thể được gán lại (*reassigned*). Nỗ lực thực hiện việc gán lại sẽ gây ra *error*:

```javascript
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // error, không thể gán lại cho hằng số (constant)!
```

Khi một lập trình viên chắc chắn rằng một *variable* sẽ không bao giờ thay đổi, họ có thể khai báo nó với `const` để đảm bảo và truyền đạt rõ ràng ý định đó cho những người khác.

### Uppercase constants (Hằng số viết hoa)

Có một thói quen thực hành (*practice*) khá phổ biến là sử dụng các *constants* như những bí danh (*aliases*) cho các giá trị khó nhớ được biết trước khi bắt đầu thực thi (*execution*).

Các *constants* như vậy được đặt tên bằng các chữ in hoa và sử dụng dấu gạch dưới (*underscores*) để tách các từ.

Ví dụ, hãy tạo ra các *constants* cho các màu sắc định dạng hex (*hex colors*):

```javascript
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...khi chúng ta cần chọn một màu sắc
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Lợi ích:
* `COLOR_ORANGE` dễ nhớ hơn rất nhiều so với `"#FF7F00"`.
* Dễ bị nhầm lẫn khi gõ `"#FF7F00"` hơn so với khi gõ `COLOR_ORANGE`.
* Khi đọc đoạn code, `COLOR_ORANGE` sẽ mang ý nghĩa biểu đạt nhiều hơn `"#FF7F00"`.

Khi nào chúng ta nên sử dụng chữ viết hoa (uppercase) cho một *constant* và khi nào thì nên gọi nó một cách thông thường? Hãy làm rõ điều này.

Là một "hằng số" (*constant*) có nghĩa là giá trị của nó sẽ không bao giờ thay đổi. Nhưng có một số *constants* được biết trước khi thực thi (*hard-coded*), và có những *constants* được tính toán (*calculated*) trong lúc chạy (*run-time*) nhưng không thay đổi giá trị sau lần gán đầu tiên.

Ví dụ:

```javascript
const pageLoadTime = /* time taken by a webpage to load */;
```

Giá trị của `pageLoadTime` không được biết trước khi tải trang web (run-time), vì vậy nó được đặt tên theo cách bình thường, không sử dụng chữ in hoa (uppercase). Nhưng nó vẫn là một *constant* vì nó không thay đổi sau khi quá trình gán giá trị được diễn ra.

Nói cách khác, các *constants* có tên được viết hoa (*capital-named constants*) chỉ được sử dụng cho các *hard-coded values* (những giá trị gán cứng, đã biết trước).

## Đặt tên một cách chính xác (Name things right)

Khi nói đến *variables*, có thêm một điều cực kỳ quan trọng cần đề cập.

Tên của một *variable* nên thể hiện ý nghĩa rõ ràng, mô tả dữ liệu mà nó đang lưu trữ.

Việc đặt tên cho *variables* là một trong những kỹ năng phức tạp và quan trọng nhất trong lập trình. Khi lướt nhanh qua code, một *variable* có cái tên tốt có thể tiết lộ ngay code đó được viết bởi một người mới (beginner) hay bởi một lập trình viên có kinh nghiệm.

Trong các dự án thực tế, phần lớn thời gian được dành cho việc sửa đổi và mở rộng bộ *code base* hiện có hơn là viết một cái gì đó hoàn toàn mới từ đầu. Khi quay trở lại với một đoạn code đã được viết sau một khoảng thời gian dài, việc tìm thông tin sẽ dễ dàng hơn nhiều nếu các *variables* được đặt tên tốt.

Hãy dành thời gian để suy nghĩ về cái tên chuẩn xác cho *variable* trước khi khai báo nó. Việc đó sẽ có ích cho bạn.

Một số nguyên tắc tốt cần tuân thủ:

* Hãy sử dụng những cái tên dễ hiểu (*human-readable*), như `userName` hoặc `shoppingCart`.
* Cố gắng tránh các chữ viết tắt hoặc các tên quá ngắn gọn như `a`, `b`, `c`, trừ khi bạn thực sự biết mình đang làm gì.
* Hãy làm cho tên có ý nghĩa tối đa và súc tích (concise). Ví dụ về những cái tên không tốt là `data` hay `value`. Những cái tên này chẳng nói lên điều gì cả. Việc sử dụng chúng chỉ chấp nhận được nếu ngữ cảnh của code làm cho ý nghĩa của *data* hoặc *value* trở nên cực kỳ rõ ràng (*exceptionally obvious*).
* Cần phải thống nhất với cách mà bản thân bạn và nhóm của bạn đặt tên, với các thuật ngữ được sử dụng. Nếu người truy cập trang web được gọi là `user`, thì chúng ta nên đặt tên cho các *variables* liên quan là `currentUser` hoặc `newUser` chứ không phải là `currentVisitor` hay `newManInTown`.

Nghe có vẻ đơn giản phải không? Đúng vậy, tuy nhiên trong thực tế thì việc tạo ra các tên biến mang tính mô tả cao và ngắn gọn lại không hề dễ dàng chút nào.

Hãy thử nghĩ xem.

**Có nên tái sử dụng lại (reuse) các variables?**
Có một số lập trình viên rất lười biếng. Thay vì khai báo một *variable* mới, họ thường có xu hướng tái sử dụng lại các *variables* hiện tại.
Kết quả là, các *variables* giống như những chiếc hộp mà mọi người hay ném đủ mọi thứ đồ đạc khác nhau vào đó mà không thay đổi *nhãn dán* của chúng. Những chiếc hộp đó sẽ chứa cái gì bên trong đây? Ai mà biết được chứ. Chúng ta phải đến lại gần và lục lọi nó.
Những lập trình viên làm như vậy chỉ tiết kiệm được một lượng thời gian rất nhỏ lúc đầu, nhưng lại đánh mất nhiều hơn thế cho việc sửa lỗi (debugging) khi một ứng dụng trở nên phức tạp.
Sẽ tốt hơn nếu bạn khai báo thêm *variable*, mỗi *variable* cho một giá trị, điều đó sẽ dễ dàng hơn cho việc bảo trì.
Hầu hết các trình tối ưu hóa cú pháp JavaScript (*minifiers and browsers*) đều đã đủ thông minh để thực hiện quá trình giải quyết rác (garbage collection) và tự động thay thế các *variables* lặp lại mà không làm giảm hiệu suất thực thi, vì vậy chúng ta không cần phải lo lắng về việc sẽ gặp lỗi phần cứng ở đây.

## Tóm tắt

Chúng ta có thể khai báo các *variables* (biến) để lưu trữ dữ liệu bằng cách sử dụng 3 từ khóa (*keywords*):
1. `let` – đại diện cho *variable* hiện đại.
2. `var` – là *variable* kiểu cũ, chúng ta không dùng đến nó trong hầu hết trường hợp, và có riêng một chương về nó với các chi tiết khác biệt.
3. `const` – giống với `let`, nhưng giá trị của *variable* không thể bị thay đổi.

Các *variables* nên được đặt theo những cái tên mà cho phép chúng ta dễ dàng hiểu được có gì đang bên trong chúng.

---

## Bài tập (Tasks)

### Làm việc với các biến (Working with variables)

Độ quan trọng: 2

1. Khai báo hai *variables*: `admin` và `name`.
2. Gán giá trị `"John"` cho `name`.
3. Sao chép (copy) giá trị từ `name` sang `admin`.
4. Hiển thị giá trị của `admin` bằng cách sử dụng `alert` (kết quả hiển thị phải là "John").

**Lời giải (Solution):**
```javascript
let admin, name; // có thể khai báo 2 biến trên cùng một dòng

name = "John";

admin = name;

alert( admin ); // "John"
```

### Đặt tên đúng (Giving the right name)

Độ quan trọng: 3

1. Tạo một *variable* với tên của hành tinh của chúng ta. Bạn sẽ đặt tên *variable* này như thế nào?
2. Tạo một *variable* lưu trữ tên của một người dùng truy cập hiện tại (*current visitor*) cho một trang web. Bạn sẽ đặt tên nó như thế nào?

**Lời giải (Solution):**
```javascript
let ourPlanetName = "Earth";
let currentUserName = "John";
```
*Lưu ý: chúng ta có thể sử dụng các tên khác, ví dụ: `earth`, `currentVisitor`.*

### Uppercase const? (Hằng số viết hoa?)

Độ quan trọng: 4

Kiểm tra đoạn mã (code) sau:
```javascript
const birthday = '18.04.1982';

const age = someCode(birthday);
```
Ở đây chúng ta có một *constant* là `birthday` (ngày sinh) và hằng số `age` (tuổi) được tính toán ra từ `birthday` bằng sự trợ giúp của một số đoạn code (code này chưa được cung cấp cụ thể vì nó không thực sự cần thiết). Tức là hằng số `age` tính từ ngày sinh đó ra tuổi ở hiện tại.

Câu hỏi: Việc sử dụng viết hoa (*uppercase*) có phù hợp với `birthday` không? Thế còn với `age` thì sao? Hoặc thậm chí là với cả hai?
```javascript
const BIRTHDAY = '18.04.1982'; // viết hoa thế này có đúng không?

const AGE = someCode(BIRTHDAY); // viết hoa thế này có đúng không?
```

**Lời giải (Solution):**

Nhìn chung, chúng ta sử dụng *uppercase* (chữ in hoa) cho các hằng số được "hard-coded" (tức là những giá trị chúng ta đã biết trước và cố định nó ngay từ trước khi thực thi (*execution*)).

Vì thế, đối với `birthday`, chúng ta nên sử dụng chữ viết hoa (uppercase), bởi vì giá trị của ngày sinh là giá trị cho trước, không thay đổi:
```javascript
const BIRTHDAY = '18.04.1982';
```
Còn đối với `age`, tuổi tác thường xuyên thay đổi qua mỗi năm, vì thế giá trị của nó được tính toán ra và nó không được biết trước trong quá trình chạy. Ở đây, hằng số `age` mang ý nghĩa chỉ là `let` nhưng giá trị không bao giờ thay đổi sau quá trình khởi tạo giá trị ban đầu. Chính vì thế chúng ta nên viết thường tên của nó thay vì sử dụng in hoa.

Tóm lại, chúng ta nên viết code như sau:
```javascript
const BIRTHDAY = '18.04.1982';

const age = someCode(BIRTHDAY);