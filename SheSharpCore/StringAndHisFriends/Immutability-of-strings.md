# [Tính bất biến của các string (Immutability of strings)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/strings/#immutability-of-strings)

String objects là immutable: chúng không thể bị thay đổi sau khi chúng được khởi tạo. Tất cả các String methods và C# operators có mặt để modify một string thực sự là trả về kết quả là **một string object mới**. Trong ví dụ dưới đây, khi nội dung của `s1` và `s2` được nối lại với nhau để tạo ra một string mới, hai string gốc không bị thay đổi. Toán tử `+=` tạo ra một new string chứa nội dung đã được nối. New object được gán lại cho biến `s1`, và object gốc mà được gán cho biến `s1` trước đó sẽ được Garbage Collection giải phóng vì không còn biến nào giữ tham chiếu của nó nữa.

```c#
string s1 = "A string is more ";
string s2 = "than the sum of its chars.";

// Concatenate s1 and s2. This actually creates a new
// string object and stores it in s1, releasing the
// reference to the original object.
s1 += s2;

System.Console.WriteLine(s1);
// Output: A string is more than the sum of its chars.
```

Vì việc chỉnh sửa một string thực ra là tạo một string mới, bạn phải thận trọng khi bạn tạo các tham chiếu tới các string. Nếu bạn tạo một tham chiếu tới một string, rồi sau đó "modify" string gốc, tham chiếu đó vẫn sẽ trỏ đến string gốc thay vì object vừa mới được tạo bởi thao tác modify của bạn. Xem xét đoạn code dưới đây đến thấy rõ hành vi này:

```c#
string str1 = "Hello ";
string str2 = str1;
str1 += "World";

System.Console.WriteLine(str2);
//Output: Hello
```

Để biết thêm thông tin về cách để tạo mới các string base vào modifications như thao tác tìm kiếm (search) và thay thế (replace) từ string gốc. Tham khảo [Cách để chỉnh sửa nội dung của chuỗi](https://learn.microsoft.com/en-us/dotnet/csharp/how-to/modify-string-contents).
