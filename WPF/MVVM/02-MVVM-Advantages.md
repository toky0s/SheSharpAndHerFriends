# MVVM – Advantages

MVVM pattern suy cho cùng nó cũng là MVC pattern nhưng hiện đại hơn, do đó về mục tiêu chính thì nó vẫn giống nhau là cung cấp một sự tách biệt rõ ràng giữa hai tầng logic và presentation. Dưới đây là một vài ưu điểm và nhược điểm của MVVM pattern.

Lợi ích chính là cho phép tách biệt rõ ràng giữa View và Model giúp code của bạn có khả năng thay đổi linh hoạt Model mà không ảnh hướng đến View và ngược lại.

Có 3 thứ quan trọng khi áp dụng MVVM như sau:

## Khả năng bảo trì

- Sự khác biệt rõ ràng giữa những phần khác nhau của code làm cho bạn dễ dàng đi vào sâu hơn những phần code và tập trung thay đổi những phần đó mà không cần lo lắng gì.
- Điều này động nghĩa với việc bạn có thể liên tục và nhanh chóng phát hành các phiên bản mới của ứng dụng.

## Khả năng kiểm thử

- Với MVVM, từng đoạn code sẽ trở nên chi tiết hơn, sự tách biệt rõ ràng giữa những phần code giúp bạn kiểm tra những phần logic cốt lõi khi muốn.
- Điều này giúp việc viết unit test trở nên đơn giản hơn nhiều.
- Đảm bảo rằng nó hoạt động một cách đúng đắn ngay cả khi có sự thay đổi trong quá trình bảo trì.

## Khả năng mở rộng

- Đôi lúc nó khả giống với khả năng bảo trì vì nó phân tách các phần với nhau rất rõ ràng và chi tiết.
- Bạn có thể dễ dàng tạo ra những phần code có thể tái sử dụng.
- Nó cũng có khả năng thay thế hoặc thêm các đoạn code mới làm những việc tương tự vào đúng vị trí trong architecture.

Rõ ràng mục đích của MVVM pattern là trừu tượng hoá View, làm giảm số lượng business logic trong code-behind. Tuy nhiên, sau đây là một lợi thế khác chắc chắn sẽ có được khi triển khai MVVM:

- ViewModel dễ dàng thực hiện unit test hoặc event-driven code hơn code-behind.
- Bạn có thể test mà không đụng đến phần tương tác UI.
- Presentation layer và logic có sự kết nối lỏng lẻo (loosely coupled).

## Bất lợi

- Có người nghĩ rằng với những UI đơn giản thì việc dùng MVVM là không cần thiết.
- Trong với các dự án lớn hơn, ViewModel có thể trở nên khó design.
- Debugging sẽ khó hơn một chút vì ta sử dụng Data Binding.

Các điểm bất lợi trên hầu hết sẽ được giải quyết khá hiệu quả bằng các IDE hiện đại như Visual Studio hay Rider.
