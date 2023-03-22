# MVVM – Giới thiệu

Để giúp kiến trúc code hợp lý và tái sử dụng code dễ dàng - MVVM ra đời. **M**odel, **V**iew và **V**iew**M**odel (MVVM pattern) nói về cách bạn tổ chức code để có thể viết ra những ứng dụng dễ bảo trì, kiểm thử và mở rộng.

- **Model** - Đơn giản là phần chứa dữ liệu, không đụng đến bất kỳ phần xử lý logic nào.
- **ViewModel** - Là phần link/connection giữa Model và View, hầu hết logic nghiệp vụ sẽ nằm ở đây.
- **View** - Chỉ đơn giản là phần dữ liệu đã được Style để hiển thị lên cho người dùng. Dữ liệu đó do phần Model quyết định.

![Giới thiệu MVVM](https://www.tutorialspoint.com/mvvm/images/view_model.jpg)

## Phân tách Presentation (Separated Presentation)

Để tránh các vấn đề phát sinh khi đặt logic ở code-behind hoặc XAML cách tốt nhất là sử dụng một kỹ thuật có tên là Separated Presentation (Phân tách Presentation). Ta giảm tối thiểu lượng code behind và XAML làm việc trực tiếp với các UI component. Các User Interface class sẽ chứa code để xử lý các hành vi tương tác phức tạp, application logic, và những thứ khác như bạn có thể thấy ở hình bên trái.

![Phân tách tầng Presentation](https://www.tutorialspoint.com/mvvm/images/separated_presentation.jpg)

- Với Separated Presentation, User Interface class sẽ đơn giản hơn nhiều. Tất nhiên là vẫn sẽ có XAML và code-behind nhưng code-behind sẽ ít đụng đến hơn.
- Application logic được tách rời thành một class riêng thường được gọi là Model.
- Tuy nhiên, đây không phải là tất cả. Nếu bạn dừng ở đây, bạn sẽ lặp lại một lỗi cực kỳ phổ biến đưa bạn xuống địa ngục của việc Data Binding khùng điên.
- Nhiều lập trình viên cố gắng sử dụng Data Binding để kết nối những element của XAML trực tiếp tới những thuộc tính của Model.
- Đôi lúc những điều này OK, nhưng thường thì không. Vấn đề ở đây là Model chỉ quan tâm đến logic nghiệp vụ, chứ không phải quan tâm đến cách mà người dùng tương tác với ứng dụng.
- Cách bạn trình bày dữ liệu thường hơi khác với cách nó được cấu trúc bên trong.
- Hơn nữa, hầu hết các User Interface có một số state không thuộc Application Model.
- Ví dụ, nếu giao diện người dùng của bạn có tính năng kéo thả, vài thứ sẽ cần được theo dõi như vị trí của item hiện đang được kéo thả, cách nó xuất hiện ra sao khi nó được kéo và thả vào vị trí cần thả,...
- Loại state này có thể trở nên phức tạp và cần được kiểm tra kỹ lưỡng.
- Trong thực tế, bạn thường muốn một số class khác nằm giữa user interface và model. Điều này có hai vai trò quan trọng:
  - Đầu tiên là nó điều chỉnh Application Model của bạn phù hợp với một User Interface View cụ thể.
  - Thứ hai, đó là nơi chứa các logic tương tác tối thiểu để UI của bạn hoạt động theo cách bạn muốn.
