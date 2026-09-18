# Kiểu dữ liệu (Data types)

Một giá trị trong JavaScript luôn thuộc về một kiểu nhất định. Ví dụ, một *string* (chuỗi) hoặc một *number* (số).

Có 8 kiểu dữ liệu (*data types*) cơ bản trong JavaScript. Ở đây, chúng ta sẽ tìm hiểu tổng quan về chúng và trong các chương tiếp theo, chúng ta sẽ nói chi tiết về từng kiểu một.

Chúng ta có thể đặt bất kỳ kiểu nào vào trong một *variable* (biến). Ví dụ, một *variable* có thể lúc này là một *string* và sau đó lại lưu trữ một *number*:

```javascript
// no error
let message = "hello";
message = 123456;
```

Các ngôn ngữ lập trình cho phép những điều như vậy, chẳng hạn như JavaScript, được gọi là "định kiểu động" (*dynamically typed*), có nghĩa là có tồn tại các kiểu dữ liệu, nhưng các *variables* không bị ràng buộc vĩnh viễn với bất kỳ kiểu nào trong số chúng.

## Number

```javascript
let n = 123;
n = 12.345;
```

Kiểu *number* đại diện cho cả số nguyên (*integer*) và số thực dấu phẩy động (*floating point numbers*).

Có rất nhiều phép toán dành cho *numbers*, ví dụ như phép nhân `*`, phép chia `/`, phép cộng `+`, phép trừ `-`, v.v.

Bên cạnh các *numbers* thông thường, còn có cái gọi là "các giá trị số đặc biệt" (*special numeric values*) cũng thuộc về kiểu dữ liệu này: `Infinity`, `-Infinity` và `NaN`.

`Infinity` đại diện cho giá trị Vô cực (Infinity $\infty$) trong toán học. Nó là một giá trị đặc biệt lớn hơn bất kỳ số nào.

Chúng ta có thể nhận được nó như là kết quả của phép chia cho không:

```javascript
alert( 1 / 0 ); // Infinity
```

Hoặc chỉ cần tham chiếu trực tiếp đến nó:

```javascript
alert( Infinity ); // Infinity
```

`NaN` đại diện cho một lỗi tính toán (*computational error*). Nó là kết quả của một phép toán học không chính xác hoặc không xác định, ví dụ:

```javascript
alert( "not a number" / 2 ); // NaN, such division is erroneous
```

`NaN` có tính chất "dính" (*sticky*). Bất kỳ phép toán nào tiếp theo thực hiện trên `NaN` đều trả về `NaN`:

```javascript
alert( NaN + 1 ); // NaN
alert( 3 * NaN ); // NaN
alert( "not a number" / 2 - 1 ); // NaN
```

Vì vậy, nếu có một `NaN` ở đâu đó trong một biểu thức toán học, nó sẽ lan truyền đến toàn bộ kết quả (chỉ có một ngoại lệ duy nhất cho điều đó: `NaN ** 0` là `1`).

**Các phép toán học là an toàn (Mathematical operations are safe)**
Làm toán học trong JavaScript là "an toàn". Chúng ta có thể làm bất cứ điều gì: chia cho 0, xử lý các chuỗi không phải số như thể chúng là các số, v.v.
*Script* sẽ không bao giờ dừng lại với một lỗi nghiêm trọng (*fatal error* hay "die"). Tệ nhất thì, chúng ta sẽ nhận được `NaN` làm kết quả.
Các giá trị số đặc biệt về mặt hình thức đều thuộc kiểu "number". Tất nhiên chúng không phải là những số theo ý nghĩa thông thường của từ này.
Chúng ta sẽ tìm hiểu thêm về cách làm việc với các *numbers* trong chương Numbers.

## BigInt

Trong JavaScript, kiểu "number" không thể biểu diễn một cách an toàn các giá trị số nguyên (*integer values*) lớn hơn $(2^{53}-1)$ (tức là `9007199254740991`), hoặc nhỏ hơn $-(2^{53}-1)$ đối với các số âm.

Để thực sự chính xác, kiểu "number" có thể lưu trữ các số nguyên lớn hơn (lên đến $1.7976931348623157 \times 10^{308}$), nhưng nằm ngoài phạm vi số nguyên an toàn (*safe integer range*) $\pm(2^{53}-1)$ sẽ có một sai số về độ chính xác (*precision error*), bởi vì không phải tất cả các chữ số đều vừa vặn với không gian lưu trữ 64-bit cố định. Do đó, một giá trị "xấp xỉ" (*approximate*) sẽ được lưu trữ thay thế.

Ví dụ, hai số này (nằm ngay phía trên phạm vi an toàn) là giống nhau:

```javascript
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

Nói cách khác, tất cả các số nguyên lẻ lớn hơn $(2^{53}-1)$ hoàn toàn không thể được lưu trữ trong kiểu "number".

Đối với hầu hết các mục đích, phạm vi $\pm(2^{53}-1)$ là khá đủ, nhưng đôi khi chúng ta cần toàn bộ phạm vi của các số nguyên thực sự rất lớn, ví dụ cho mật mã học (*cryptography*) hoặc các dấu thời gian có độ chính xác đến micro-giây (*microsecond-precision timestamps*).

Kiểu `BigInt` mới được thêm vào ngôn ngữ gần đây để đại diện cho các số nguyên có độ dài tùy ý.

Một giá trị `BigInt` được tạo ra bằng cách thêm `n` vào cuối của một số nguyên:

```javascript
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

Vì các số `BigInt` hiếm khi cần thiết, chúng ta sẽ không trình bày chi tiết về chúng ở đây, mà dành riêng cho chúng một chương biệt lập là BigInt. Hãy đọc nó khi bạn cần đến những con số lớn như vậy.

## String

Một *string* (chuỗi) trong JavaScript phải được bao quanh bởi các dấu ngoặc kép (*quotes*).

```javascript
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
```

Trong JavaScript, có 3 loại *quotes*.

1. Ngoặc kép (*Double quotes*): `"Hello"`.
2. Ngoặc đơn (*Single quotes*): `'Hello'`.
3. Dấu Backticks: `` `Hello` ``.

Ngoặc kép và ngoặc đơn là những *quotes* "đơn giản" (*simple quotes*). Thực tế không có sự khác biệt nào giữa chúng trong JavaScript.

Dấu backticks là các *quotes* có "chức năng mở rộng" (*extended functionality quotes*). Chúng cho phép chúng ta nhúng (*embed*) các *variables* và các biểu thức (*expressions*) vào một *string* bằng cách bọc chúng trong `${…}`, ví dụ:

```javascript
let name = "John";

// embed a variable
alert( `Hello, ${name}!` ); // Hello, John!

// embed an expression
alert( `the result is ${1 + 2}` ); // the result is 3
```

Biểu thức bên trong `${…}` được tính toán (*evaluated*) và kết quả trở thành một phần của *string*. Chúng ta có thể đặt bất cứ thứ gì vào đó: một *variable* như `name` hoặc một biểu thức số học như `1 + 2` hoặc một cái gì đó phức tạp hơn.

Xin lưu ý rằng điều này chỉ có thể được thực hiện trong backticks. Các *quotes* khác không có chức năng *embedding* (nhúng) này!

```javascript
alert( "the result is ${1 + 2}" ); // the result is ${1 + 2} (double quotes do nothing)
```

Chúng ta sẽ tìm hiểu về *strings* kỹ hơn trong chương Strings.

**Không có kiểu ký tự (There is no character type)**
Trong một số ngôn ngữ, có một kiểu đặc biệt "character" dành cho một ký tự đơn lẻ. Ví dụ, trong ngôn ngữ C và Java, nó được gọi là "char".
Trong JavaScript, không có kiểu như vậy. Chỉ có một kiểu duy nhất: `string`. Một *string* có thể bao gồm không có ký tự nào (chuỗi rỗng), 1 ký tự hoặc nhiều ký tự.

## Boolean (kiểu logic)

Kiểu *boolean* chỉ có hai giá trị: `true` (đúng) và `false` (sai).

Kiểu này thường được sử dụng để lưu trữ các giá trị yes/no: `true` có nghĩa là "có, đúng", và `false` có nghĩa là "không, sai".

Ví dụ:

```javascript
let nameFieldChecked = true; // yes, name field is checked
let ageFieldChecked = false; // no, age field is not checked
```

Các giá trị *boolean* cũng đến từ kết quả của các phép so sánh (*comparisons*):

```javascript
let isGreater = 4 > 1;

alert( isGreater ); // true (the comparison result is "yes")
```

Chúng ta sẽ tìm hiểu về *booleans* sâu hơn trong chương Logical operators.

## Giá trị "null"

Giá trị đặc biệt `null` không thuộc về bất kỳ kiểu nào được mô tả ở trên.

Nó tạo thành một kiểu riêng biệt của chính nó, chỉ chứa giá trị `null`:

```javascript
let age = null;
```

Trong JavaScript, `null` không phải là một "tham chiếu đến một đối tượng không tồn tại" (*reference to a non-existing object*) hoặc một "con trỏ null" (*null pointer*) như trong một số ngôn ngữ khác.

Nó chỉ là một giá trị đặc biệt đại diện cho "không có gì", "rỗng" hoặc "giá trị không xác định" (*value unknown*).

Đoạn code trên tuyên bố rằng `age` là không xác định.

## Giá trị "undefined"

Giá trị đặc biệt `undefined` cũng đứng tách biệt. Nó tạo thành một kiểu riêng của chính nó, giống như `null`.

Ý nghĩa của `undefined` là "giá trị chưa được gán" (*value is not assigned*).

Nếu một *variable* được khai báo, nhưng không được gán, thì giá trị của nó là `undefined`:

```javascript
let age;

alert(age); // shows "undefined"
```

Về mặt kỹ thuật, hoàn toàn có thể gán giá trị `undefined` cho một *variable* một cách rõ ràng (*explicitly*):

```javascript
let age = 100;

// change the value to undefined
age = undefined;

alert(age); // "undefined"
```

…Nhưng chúng tôi không khuyến khích làm điều đó. Thông thường, người ta sử dụng `null` để gán một giá trị "rỗng" hoặc "không xác định" cho một *variable*, trong khi `undefined` được dành riêng làm giá trị khởi tạo mặc định (*default initial value*) cho những thứ chưa được gán.

## Objects và Symbols

Kiểu `object` là một kiểu đặc biệt.

Tất cả các kiểu khác được gọi là "nguyên thủy" (*primitive*) vì các giá trị của chúng chỉ có thể chứa một thứ duy nhất (cho dù nó là một *string* hay một *number* hay bất cứ thứ gì). Ngược lại, các *objects* được sử dụng để lưu trữ các tập hợp dữ liệu (*collections of data*) và các thực thể phức tạp hơn.

Bởi vì nó rất quan trọng, các *objects* xứng đáng được đối xử theo cách đặc biệt. Chúng ta sẽ giải quyết chúng sau trong chương Objects, sau khi chúng ta đã tìm hiểu thêm về các *primitives*.

Kiểu `symbol` được sử dụng để tạo các định danh duy nhất (*unique identifiers*) cho các *objects*. Chúng ta phải đề cập đến nó ở đây để cho hoàn thiện, nhưng cũng sẽ hoãn lại các chi tiết cho đến khi chúng ta biết về *objects*.

## Toán tử typeof (The typeof operator)

Toán tử `typeof` (*typeof operator*) trả về kiểu dữ liệu của một toán hạng (*operand*). Nó rất hữu ích khi chúng ta muốn xử lý các giá trị của các kiểu khác nhau theo những cách khác nhau hoặc chỉ muốn kiểm tra nhanh.

Việc gọi `typeof x` trả về một *string* chứa tên của kiểu dữ liệu:

```javascript
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

typeof Math // "object"  (1)

typeof null // "object"  (2)

typeof alert // "function"  (3)
```

Ba dòng cuối cùng có thể cần được giải thích thêm:

1. `Math` là một đối tượng tích hợp sẵn (*built-in object*) chuyên cung cấp các phép toán học. Chúng ta sẽ học nó trong chương Numbers. Ở đây, nó chỉ đóng vai trò như một ví dụ về một *object*.
2. Kết quả của `typeof null` là `"object"`. Đó là một lỗi được công nhận chính thức trong `typeof`, bắt nguồn từ những ngày đầu tiên của JavaScript và được giữ lại vì tính tương thích (*compatibility*). Chắc chắn rồi, `null` không phải là một *object*. Nó là một giá trị đặc biệt mang một kiểu riêng biệt của nó. Hành vi của `typeof` bị sai ở chỗ này.
3. Kết quả của `typeof alert` là `"function"`, bởi vì `alert` là một hàm (*function*). Chúng ta sẽ nghiên cứu về các *functions* trong các chương tiếp theo, nơi chúng ta cũng sẽ thấy rằng không có kiểu "function" đặc biệt nào trong JavaScript cả. Các *functions* thuộc về kiểu `object`. Nhưng `typeof` đối xử với chúng khác biệt đi và trả về `"function"`. Điều đó cũng bắt nguồn từ những ngày đầu của JavaScript. Về mặt kỹ thuật, hành vi như vậy không đúng, nhưng có thể rất tiện lợi trong thực tế.

**Cú pháp `typeof(x)`**
Bạn cũng có thể bắt gặp một cú pháp khác: `typeof(x)`. Nó giống hệt như `typeof x`.
Để làm rõ ràng hơn: `typeof` là một toán tử (*operator*), không phải là một hàm (*function*). Dấu ngoặc đơn ở đây không phải là một phần của `typeof`. Đó là loại dấu ngoặc đơn được sử dụng cho việc nhóm các phép toán (*mathematical grouping*).
Thông thường, các dấu ngoặc đơn đó chứa một biểu thức toán học, chẳng hạn như `(2 + 2)`, nhưng ở đây chúng chỉ chứa một đối số (*argument*) là `(x)`. Về mặt cú pháp, chúng cho phép tránh một khoảng trắng giữa toán tử `typeof` và *argument* của nó, và một số người thích điều đó.
Một số người thích `typeof(x)`, mặc dù cú pháp `typeof x` phổ biến hơn nhiều.

## Tóm tắt

Có 8 kiểu dữ liệu (*data types*) cơ bản trong JavaScript.

Bảy kiểu dữ liệu nguyên thủy (*primitive data types*):
* `number` dùng cho các số dưới bất kỳ hình thức nào: số nguyên hoặc dấu phẩy động, các số nguyên bị giới hạn bởi $\pm(2^{53}-1)$.
* `bigint` dùng cho các số nguyên có độ dài tùy ý.
* `string` dùng cho các chuỗi. Một *string* có thể có 0 hoặc nhiều ký tự, không có kiểu dữ liệu riêng biệt nào dành cho một ký tự đơn lẻ.
* `boolean` cho `true` / `false`.
* `null` cho các giá trị không xác định – một kiểu độc lập (*standalone type*) chỉ có một giá trị duy nhất là `null`.
* `undefined` cho các giá trị chưa được gán – một kiểu độc lập chỉ có một giá trị duy nhất là `undefined`.
* `symbol` dùng cho các định danh duy nhất (*unique identifiers*).

Và một kiểu dữ liệu không nguyên thủy (*non-primitive data type*):
* `object` dành cho các cấu trúc dữ liệu phức tạp hơn.

Toán tử `typeof` cho phép chúng ta xem kiểu dữ liệu nào đang được lưu trữ trong một *variable*.
* Thường được sử dụng dưới dạng `typeof x`, nhưng `typeof(x)` cũng được cho phép.
* Trả về một *string* có chứa tên của kiểu, chẳng hạn như `"string"`.
* Đối với `null` nó sẽ trả về `"object"` – đây là một lỗi trong ngôn ngữ, thực chất nó không phải là một *object*.

Trong các chương tiếp theo, chúng ta sẽ tập trung vào các giá trị nguyên thủy (*primitive values*) và sau khi chúng ta đã quen thuộc với chúng, chúng ta sẽ chuyển sang *objects*.

---

## Bài tập (Tasks)

### String quotes

Độ quan trọng: 5

Kết quả đầu ra của đoạn *script* này là gì?

```javascript
let name = "Ilya";

alert( `hello ${1}` ); // ?

alert( `hello ${"name"}` ); // ?

alert( `hello ${name}` ); // ?
```

**Lời giải (Solution)**

Dấu backticks nhúng biểu thức (*expression*) bên trong `${...}` vào *string*.

```javascript
let name = "Ilya";

// the expression is a number 1
alert( `hello ${1}` ); // hello 1

// the expression is a string "name"
alert( `hello ${"name"}` ); // hello name

// the expression is a variable, embed it
alert( `hello ${name}` ); // hello Ilya
```