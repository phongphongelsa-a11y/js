# Giới thiệu về JavaScript

Hãy cùng xem JavaScript có gì đặc biệt, chúng ta có thể làm được gì với nó, và những công nghệ nào khác hoạt động tốt cùng với nó.

## JavaScript là gì?

JavaScript ban đầu được tạo ra để "làm cho các trang web trở nên sống động".

Các chương trình trong ngôn ngữ này được gọi là các *scripts*. Chúng có thể được viết trực tiếp vào HTML của trang web và tự động chạy khi trang web tải.

Các scripts được cung cấp và thực thi dưới dạng văn bản thuần túy (plain text). Chúng không cần bất kỳ sự chuẩn bị đặc biệt hay quá trình biên dịch (*compilation*) nào để chạy.

Ở khía cạnh này, JavaScript rất khác biệt so với một ngôn ngữ khác có tên là Java.

## Tại sao nó được gọi là JavaScript?

Khi JavaScript được tạo ra, ban đầu nó có một tên khác: "LiveScript". Nhưng vào thời điểm đó Java đang rất phổ biến, do vậy người ta quyết định rằng việc định vị một ngôn ngữ mới như một "người em trai" của Java sẽ giúp ích cho sự phát triển của nó.

Nhưng trong quá trình phát triển, JavaScript đã trở thành một ngôn ngữ hoàn toàn độc lập với một đặc tả (*specification*) riêng gọi là ECMAScript, và hiện tại nó không còn bất kỳ mối liên hệ nào với Java.

Ngày nay, JavaScript không chỉ có thể thực thi trong trình duyệt (*browser*), mà còn trên máy chủ (*server*), hay thực tế là trên bất kỳ thiết bị nào có chứa một chương trình đặc biệt được gọi là *JavaScript engine*.

Trình duyệt có một engine được nhúng sẵn, đôi khi được gọi là "máy ảo JavaScript" (*JavaScript virtual machine*).

Các engines khác nhau có các "tên mã" (*codenames*) khác nhau. Ví dụ:

*   **V8** – trong Chrome, Opera và Edge.
*   **SpiderMonkey** – trong Firefox.
*   …Có các codenames khác như "Chakra" cho IE, "JavaScriptCore", "Nitro" và "SquirrelFish" cho Safari, v.v.

Bạn nên ghi nhớ các thuật ngữ ở trên vì chúng thường được sử dụng trong các bài viết của developer trên internet. Chúng ta cũng sẽ sử dụng chúng. Ví dụ, nếu "một tính năng X được hỗ trợ bởi V8", thì nó có thể sẽ hoạt động trong Chrome, Opera và Edge.

## Các engines hoạt động như thế nào?

Các engines khá phức tạp, nhưng những nguyên lý cơ bản lại rất đơn giản.

1.  Engine (được nhúng nếu nó là một trình duyệt) đọc (*parses*) script.
2.  Sau đó, nó chuyển đổi (*compiles*) script thành mã máy (*machine code*).
3.  Và cuối cùng machine code chạy, cực kỳ nhanh.

Engine áp dụng các tối ưu hóa ở mỗi bước của quy trình. Nó thậm chí còn theo dõi script đã được compile trong khi chạy, phân tích dữ liệu chảy qua nó, và tiếp tục tối ưu hóa machine code dựa trên những kiến thức thu thập được.

## JavaScript trong trình duyệt có thể làm gì?

JavaScript hiện đại là một ngôn ngữ lập trình "an toàn". Nó không cung cấp quyền truy cập cấp thấp (*low-level access*) vào bộ nhớ hoặc CPU, vì ban đầu nó được tạo ra cho các trình duyệt vốn không yêu cầu điều đó.

Khả năng của JavaScript phụ thuộc rất nhiều vào môi trường (*environment*) mà nó đang chạy. Ví dụ, Node.js hỗ trợ các hàm cho phép JavaScript đọc/ghi các file tùy ý, thực hiện các network requests, v.v.

JavaScript trong trình duyệt có thể làm mọi thứ liên quan đến thao tác trên trang web, tương tác với người dùng và máy chủ web (*webserver*).

Ví dụ, JavaScript trong trình duyệt có khả năng:

*   Thêm HTML mới vào trang, thay đổi nội dung hiện có, chỉnh sửa styles.
*   Phản hồi lại các hành động của người dùng, chạy khi có thao tác nhấp chuột, di chuyển con trỏ, nhấn phím.
*   Gửi các requests qua mạng tới các máy chủ từ xa (*remote servers*), tải xuống và tải lên các file (được gọi là công nghệ AJAX và COMET).
*   Lấy và thiết lập *cookies*, đặt câu hỏi cho khách truy cập, hiển thị thông báo.
*   Ghi nhớ dữ liệu ở phía client (*local storage*).

## JavaScript trong trình duyệt KHÔNG THỂ làm gì?

Khả năng của JavaScript trong trình duyệt bị giới hạn để bảo vệ an toàn cho người dùng. Mục đích là để ngăn chặn một trang web độc hại truy cập vào thông tin cá nhân hoặc làm hỏng dữ liệu của người dùng.

Các ví dụ về những hạn chế này bao gồm:

*   JavaScript trên một trang web không thể tự ý đọc/ghi các file trên ổ cứng, sao chép chúng hoặc thực thi các chương trình. Nó không có quyền truy cập trực tiếp vào các chức năng của hệ điều hành (*OS functions*).

    Các trình duyệt hiện đại cho phép nó làm việc với các file, nhưng quyền truy cập bị hạn chế và chỉ được cung cấp nếu người dùng thực hiện một số hành động nhất định, như "kéo thả" một file vào cửa sổ trình duyệt hoặc chọn nó thông qua thẻ `<input>`.

*   Có những cách để tương tác với camera/microphone và các thiết bị khác, nhưng chúng đòi hỏi sự cho phép rõ ràng từ người dùng. Vì vậy, một trang web có bật JavaScript không thể lén lút bật web-camera, quan sát xung quanh và gửi thông tin đến NSA.

*   Các tabs/cửa sổ khác nhau nói chung không biết về sự tồn tại của nhau. Đôi khi chúng có thể, ví dụ như khi một cửa sổ sử dụng JavaScript để mở một cửa sổ khác. Nhưng ngay cả trong trường hợp này, JavaScript từ trang này không thể truy cập vào trang kia nếu chúng đến từ các trang web khác nhau (từ một *domain, protocol*, hoặc *port* khác nhau).

    Điều này được gọi là "Same Origin Policy". Để giải quyết vấn đề đó, cả hai trang phải đồng ý trao đổi dữ liệu và phải chứa đoạn mã JavaScript đặc biệt để xử lý việc đó. Chúng ta sẽ tìm hiểu về nó trong phần sau của tutorial.

    Hạn chế này, một lần nữa, là vì sự an toàn của người dùng. Một trang từ `http://anysite.com` mà người dùng đã mở sẽ không được phép truy cập vào một tab trình duyệt khác có URL là `http://gmail.com`, và đánh cắp thông tin từ đó.

*   JavaScript có thể dễ dàng giao tiếp qua mạng với server nơi cung cấp trang hiện tại. Nhưng khả năng nhận dữ liệu từ các sites/domains khác bị hạn chế nghiêm trọng. Mặc dù có thể làm được, nhưng nó đòi hỏi sự đồng ý rõ ràng (được thể hiện qua *HTTP headers*) từ phía remote. Một lần nữa, đó là một giới hạn an toàn.

Những hạn chế như vậy không tồn tại nếu JavaScript được sử dụng bên ngoài trình duyệt, ví dụ như trên một server. Các trình duyệt hiện đại cũng cho phép các *plugins/extensions*, chúng có thể yêu cầu thêm các quyền mở rộng.

## Điều gì làm cho JavaScript trở nên độc đáo?

Có ít nhất ba điều tuyệt vời về JavaScript:

1.  Tích hợp hoàn toàn với HTML/CSS.
2.  Những điều đơn giản được thực hiện một cách đơn giản.
3.  Được hỗ trợ bởi tất cả các trình duyệt lớn (*major browsers*) và được bật mặc định.

JavaScript là công nghệ trình duyệt duy nhất kết hợp được ba yếu tố này.

Đó là điều làm cho JavaScript trở nên độc đáo. Đó là lý do tại sao nó là công cụ phổ biến nhất để tạo ra các giao diện trình duyệt (*browser interfaces*).

Tuy nhiên, JavaScript cũng có thể được sử dụng để tạo servers, ứng dụng di động (*mobile applications*), v.v.

## Các ngôn ngữ "nằm trên" JavaScript

Cú pháp (*syntax*) của JavaScript không phù hợp với nhu cầu của tất cả mọi người. Những người khác nhau muốn những tính năng khác nhau.

Điều đó là dễ hiểu, vì các projects và yêu cầu đối với mỗi người là khác nhau.

Vì vậy, gần đây có rất nhiều ngôn ngữ mới xuất hiện, chúng được *transpiled* (chuyển đổi) sang JavaScript trước khi chạy trong trình duyệt.

Các công cụ hiện đại làm cho việc *transpilation* trở nên rất nhanh và trong suốt, thực tế cho phép các developers code bằng một ngôn ngữ khác và tự động chuyển đổi nó "under the hood" (âm thầm ở bên dưới).

Ví dụ về những ngôn ngữ như vậy:

*   **CoffeeScript** là một "syntactic sugar" cho JavaScript. Nó giới thiệu syntax ngắn gọn hơn, cho phép chúng ta viết code rõ ràng và chính xác hơn. Thông thường, các Ruby devs rất thích nó.
*   **TypeScript** tập trung vào việc bổ sung "strict data typing" (kiểu dữ liệu nghiêm ngặt) để đơn giản hóa quá trình phát triển và hỗ trợ các hệ thống phức tạp. Nó được phát triển bởi Microsoft.
*   **Flow** cũng bổ sung data typing, nhưng theo một cách khác. Được phát triển bởi Facebook.
*   **Dart** là một ngôn ngữ độc lập có engine riêng chạy trong các môi trường không phải trình duyệt (như mobile apps), nhưng cũng có thể được *transpiled* sang JavaScript. Được phát triển bởi Google.
*   **Brython** là một *transpiler* từ Python sang JavaScript, cho phép viết các ứng dụng bằng Python thuần mà không cần đến JavaScript.
*   **Kotlin** là một ngôn ngữ lập trình hiện đại, súc tích và an toàn, có thể *target* đến trình duyệt hoặc Node.

Vẫn còn nhiều ngôn ngữ khác. Tất nhiên, ngay cả khi chúng ta sử dụng một trong những ngôn ngữ được *transpiled* này, chúng ta cũng nên biết JavaScript để thực sự hiểu những gì chúng ta đang làm.

## Tóm tắt

*   JavaScript ban đầu được tạo ra như một ngôn ngữ chỉ dành cho trình duyệt, nhưng hiện nay nó cũng được sử dụng trong nhiều môi trường khác.
*   Ngày nay, JavaScript có một vị trí độc tôn vì là ngôn ngữ trình duyệt được áp dụng rộng rãi nhất, tích hợp hoàn toàn với HTML/CSS.
*   Có rất nhiều ngôn ngữ được *transpiled* sang JavaScript và cung cấp các tính năng nhất định. Khuyến nghị bạn nên xem qua chúng, ít nhất là một cách ngắn gọn, sau khi đã thành thạo (*mastering*) JavaScript.