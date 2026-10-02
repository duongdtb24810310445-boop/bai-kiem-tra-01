# Câu 1

**Value Types (kiểu giá trị)** là kiểu dữ liệu mà biến lưu trực tiếp giá trị của nó. Khi gán một biến kiểu giá trị cho biến khác, giá trị được sao chép sang biến mới nên hai biến hoạt động độc lập. Các kiểu như `int`, `double`, `bool`, `struct` thuộc nhóm này. Dữ liệu của Value Type thường được lưu trên Stack khi là biến cục bộ, nhưng có thể nằm trên Heap nếu là thành phần của một đối tượng.

**Reference Types (kiểu tham chiếu)** là kiểu dữ liệu mà biến lưu một tham chiếu đến đối tượng chứa dữ liệu. Đối tượng thường được cấp phát trên Heap và được quản lý bởi Garbage Collector. Khi gán một biến Reference Type cho biến khác, hai biến có thể cùng tham chiếu đến một đối tượng nên thay đổi đối tượng thông qua một biến có thể ảnh hưởng đến biến còn lại.

---

# Câu 2

**Init-only Properties (`init`)** cho phép một thuộc tính chỉ được thiết lập giá trị trong quá trình khởi tạo đối tượng và không thể thay đổi bằng cách gán thông thường sau khi đối tượng đã được tạo.

Trong khi đó, thuộc tính sử dụng **`set`** cho phép thiết lập và thay đổi giá trị bất kỳ lúc nào trong phạm vi mà thuộc tính cho phép.

`init` thường được sử dụng khi muốn một số thông tin của đối tượng cố định sau khi khởi tạo, giúp hạn chế việc thay đổi dữ liệu ngoài ý muốn và làm cho đối tượng an toàn hơn về mặt trạng thái.

---

# Câu 3

**`virtual`** là từ khóa được sử dụng ở phương thức của lớp cha, cho phép phương thức đó được lớp con thay đổi cách triển khai.

**`override`** được sử dụng ở lớp con để ghi đè và cung cấp cách triển khai mới cho phương thức `virtual` của lớp cha.

Hai từ khóa này kết hợp với nhau để thực hiện tính đa hình (**Polymorphism**). Nhờ đó, khi chương trình làm việc với đối tượng thông qua kiểu của lớp cha, phương thức được thực thi có thể phụ thuộc vào kiểu thực tế của đối tượng lớp con.

---

# Câu 4

Một thành phần được khai báo **`static`** thuộc về lớp (**Class**) chứ không thuộc về từng đối tượng được tạo ra từ lớp đó.

Khi sử dụng `static`, thành phần đó chỉ tồn tại một bản dùng chung cho toàn bộ lớp, thay vì mỗi Object Instance có một bản riêng. Vì vậy, thành phần `static` được truy xuất thông qua tên lớp, không thông qua một đối tượng được tạo bằng `new`.

Điều này giúp sử dụng các dữ liệu hoặc phương thức mang tính dùng chung cho tất cả các đối tượng mà không cần tạo đối tượng cụ thể.

