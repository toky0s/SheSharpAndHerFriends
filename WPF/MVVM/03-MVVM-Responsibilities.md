# Trách nhiệm của từng phần trong MVVM

MVVM pattern có ba phần - Model, View và ViewModel. Hầu hết các dev khi bắt đầu đều hơi bối rối về chuyện Model, View và ViewModel nên chứa gì và không nên chứa gì và nhiệm vụ của từng phần là gì.

Trong bài viết này ta sẽ nói về trách nhiệm của từng phần trong MVVM pattern để bạn có cái nhìn rõ ràng nhất về chuyện nên đặt code của bạn ở đâu. MVVM thực ra là một kiến trúc phân tầng (layered architecture) cho phía client được thể hiện bởi hình dưới đây:

![mvvm_responsibilities](https://www.tutorialspoint.com/mvvm/images/mvvm_responsibilities.jpg)

- Presentation layer bao gồm các View.
- Logical layer là các ViewModel.
- Data layer là kết hợp của các model object.
- Client service khởi tạo (produce) và duy trỳ (persist) chúng bằng hai cách:
  - Một là: Truy cập trực tiếp vào một two-tier application
  - Hai là: Thông qua các cuộc gọi service rồi sau đó đến ứng dụng của bạn.

## Trách nhiệm của Model

Nhìn chung, Model là phần dễ hiểu nhất. Đây là data model phía client dùng để hỗ trợ các view trong ứng dụng.

- Nó bao gồm các object chứa các thuộc tính và một số biến để chứa dữ liệu trong bộ nhớ.
- Những thuộc tính đó có thể tham chiếu đến các object khác của model và tạo ra object graph. Cuối cùng sẽ tạo ra một thứ gọi là các Model Object.
- Model object sẽ phát (raise) ra các thông báo khi Property Changed hay trong WPF ta thường quen với thuật ngữ là Data Binding.
- Trách nhiệm cuối cùng là validation (có hoặc không tuỳ bạn), nhưng bạn có thể nhúng validation information vào model object bằng cách sử dụng WPF data binding validation feature thông qua các interface như **INodifyDataErrorInfo**/**IDataErrorInfo**.

## Trách nhiệm của View

Mục đích và trách nhiệm chính của View là định nghĩa những cấu trúc mà người dùng có thể nhìn thấy trên màn hình. Cấu trúc có thể chứa các phần tĩnh static và động dynamic.

- Phần tĩnh là cấu trúc phân cấp XAML định nghĩa các control và layout của chúng.
- Phần động như các animation hoặc thay đổi trạng thái được xem như một phần của View.
- Mục đích chính của MVVM là không có code-behind bên trong View.
- Tuy không có code-behind bên trong view. Nhưng bạn cần ít nhất một constructor và một dòng code để gọi initialize component.
- Ý tưởng ở đây là logic code xử lý sự kiện, action và thao tác dữ liệu không nên nằm ở code-behind ở bên trong View.
- Ngoài ra đoạn code nào phải đi vào trong code-behind hay bất cứ thằng code nào trong số đó mà tham chiếu tới một UI element cũng đều được xem là View code.

## Trách nhiệm của ViewModel

- ViewModel là phần chính của MVVM application. Trách nhiệm chính của ViewModel là đưa data tới phần View, nhờ đó View có thể hiển thị data lên màn hình.
- Nó cũng cho phép người dùng tương tác với data hoặc thay đổi data.
- Một trách nhiệm quan trọng khác của ViewModel là đóng gói (encapsulate) interaction logic (code xử lý phần tương tác) của một View nào đó, nhưng nó không có nghĩa là tất cả logic của một ứng dụng nên để trong ViewModel.
- Nó có thể xử lý các cuộc gọi trình tự một cách thích hợp để làm đúng những thứ ta cần dựa trên thay đổi của người dùng hoặc bất cứ thay đổi nào trong View.
- ViewModel cũng nên quản lý các navigation logic như quyết định khi nào là lúc để điều hướng đến một View khác.
