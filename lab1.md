# LAB 1: PHÂN TÍCH KIẾN TRÚC, CƠ CHẾ, CA SỬ DỤNG

## 1. Phân tích kiến trúc

- **Kiến trúc được đề xuất:** *Kiến trúc 3 Tầng (3-Tier Architecture)*

- **Giải thích:**
  - **Phân chia nhiệm vụ rõ ràng:** Các thành phần trong kiến trúc được phân chia nhiệm vụ cụ thể, giúp quá trình bảo trì và nâng cấp dễ dàng mà không làm ảnh hưởng đến toàn hệ thống.
  - **Cải thiện bảo mật:** Tầng Xử lý Nghiệp vụ là tầng duy nhất có quyền truy cập trực tiếp vào Tầng Truy cập Dữ liệu, giúp tránh được truy cập không an toàn từ người dùng.
  - **Dễ mở rộng:** Các tầng có thể hoạt động độc lập, dễ dàng mở rộng mà không làm thay đổi toàn bộ cấu trúc hệ thống.
  - **Tổ chức tốt:** Dữ liệu, logic xử lý, và giao diện người dùng được phân tách rõ ràng, hỗ trợ bảo trì, phát triển, và quản lý dễ dàng.

- **Mô tả các thành phần trong kiến trúc:**
  - **Tầng Giao diện (Presentation Layer):** Tầng mà người dùng trực tiếp tương tác với hệ thống. Nó có trách nhiệm thu thập dữ liệu từ người dùng và hiển thị kết quả từ hệ thống.
  - **Tầng Xử lý Nghiệp vụ (Business Logic Layer):** Tầng chứa toàn bộ quy trình nghiệp vụ, xử lý dữ liệu từ giao diện, và trả kết quả cho giao diện. Tầng này kiểm tra tính hợp lệ của dữ liệu và áp dụng các quy tắc nghiệp vụ.
  - **Tầng Truy cập Dữ liệu (Data Access Layer):** Chịu trách nhiệm kết nối, truy vấn và cập nhật cơ sở dữ liệu.
  - **Tầng Tái sử dụng (Base Reuse Layer):** Cung cấp các dịch vụ và hàm tiện ích dùng chung cho các tầng khác, gồm các công cụ hỗ trợ, hàm tiện ích không phụ thuộc vào logic nghiệp vụ như mã hóa, log, và xử lý định dạng ngày tháng.

## 2. Cơ chế phân tích

- **Lưu trữ bền vững (Persistency):** Dữ liệu như thông tin nhân viên, lịch làm việc, và thông tin lương cần được lưu trữ ổn định trong cơ sở dữ liệu để bảo đảm truy xuất lịch sử và tránh mất mát.
- **Trao đổi thông tin (Communication):** Hệ thống có khả năng giao tiếp nội bộ và với hệ thống bên ngoài (ví dụ: ngân hàng để chuyển lương).
- **Chuyển đổi định dạng dữ liệu (Information Exchange and Format Conversion):** Hệ thống có khả năng trao đổi thông tin với phần mềm khác (kế toán hoặc quản lý nhân sự) và chuyển đổi định dạng dữ liệu, giúp hệ thống tương tác và tích hợp tốt hơn.
- **Bảo mật (Security):** Bảo vệ dữ liệu cá nhân và tài chính của nhân viên qua các biện pháp như mã hóa, xác thực, và phân quyền truy cập.
- **Phát hiện và xử lý lỗi (Error Detection/Handling/Reporting):** Cơ chế phát hiện lỗi khi tính lương hoặc trao đổi dữ liệu và cung cấp thông báo lỗi rõ ràng để xử lý kịp thời, duy trì sự ổn định của hệ thống.
- **Giao tiếp với hệ thống cũ (Legacy Interface):** Hệ thống mới có khả năng tương tác với cơ sở dữ liệu hiện có mà không làm thay đổi hoặc mất dữ liệu cũ.

## 3. Phân Tích Ca Sử Dụng Thanh Toán (Payment)

### 3.1. Định Nghĩa Các Lớp Phân Tích
- **Ranh Giới (Boundary):**
  + **Giao Diện Nhân Viên (EmployeeUI):** Chịu trách nhiệm giao tiếp với nhân viên, cho phép họ chọn phương thức thanh toán phù hợp.

- **Điều Khiển (Control):**
  + **Quản Lý Thanh Toán (PaymentController):** Điều phối các thao tác liên quan đến việc chọn phương thức thanh toán của nhân viên.

- **Thực Thể (Entity):**
  + Đại diện cho thông tin của nhân viên trong hệ thống, bao gồm các dữ liệu cá nhân và các thuộc tính liên quan đến phương thức thanh toán.

### 3.2. Biểu Đồ Thứ Tự (Sequence Diagram)
![Biểu Đồ Tuần Tự Thanh Toán](https://www.planttext.com/api/plantuml/png/b991JiCm44NtFiKiYzHU80jKgMBH1QKIwW4czXGiR8-n9qWv6mkEn1Lmb4GaRQN0TkQ_-JFV_lxyscR198rt2hLmWWSV7RT4fxsAfM6rZHW4ZjXw2hBZ88cTepJhZf1IlpXixg-f2XAzDvHbw3oIlB9PtQahPOUFmofueJcH2p9sONFRoTaim6V03xGEQqSGUn7uViOjqudhQL-1iJawR0VXKnJBeVE-k7EAb5MVoP4MCfT7BeOJ4slAUSRrmuhlAWzZ-_eQq9XKr6keCRmTq5CfQSrDa4FZQqgBgJRHeD1yo_-RBBs3vd2soMDtmzyZtqse4jsMWka-wGy0003__mC0)

### 3.3. Biểu Đồ Lớp (Class Diagram)
![Biểu Đồ Lớp Thanh Toán](https://www.planttext.com/api/plantuml/png/V59BJiGm3Dtd55s2rBb05sWan8850zA80tWICqJaH-miAiJ9M70aha3JDgEcHMHdFx_dvwVyV7tlYI5oiaP80qJDdGt6zuZDXsZoqwfhZXorEq-r0ujr9q1lqV43ygjV3ODI4OdgvWdSss6Z0bBwvFYGx0bZ3H4QbFoqN7DrFK4fA61SGvzYTSppVJadudj2-bjCQGe6-Xbx3AozemAUaO-Z3rJ_aM-zUz7HGkOkdSoS0UReZS5O30swbTvbOOXU3jbLuEGWIzknRal2xINLjavojB28ORUxsNhfcaH8OkinJnToDuTDOezEvG_p2m00__y30000)

### Giải Thích

#### Lớp Nhân Viên (Employee)
- **Mô Tả:** Đại diện cho thông tin cá nhân của nhân viên trong hệ thống.
- **Thuộc Tính:**
  + `id`: Mã định danh duy nhất cho mỗi nhân viên, dùng để phân biệt giữa các nhân viên khác nhau.
  + `name`: Tên của nhân viên, giúp người dùng nhận diện.
  + `paymentMethod`: Phương thức thanh toán hiện tại của nhân viên, có thể là "pick up", "mail", hoặc "direct deposit".
  + `address`: Địa chỉ mà séc sẽ được gửi đến nếu nhân viên chọn phương thức "mail".
  + `bankName`: Tên ngân hàng được chỉ định nếu nhân viên chọn phương thức "direct deposit".
  + `accountNumber`: Số tài khoản ngân hàng của nhân viên để thực hiện chuyển khoản nếu chọn "direct deposit".

- **Phương Thức:**
  + `selectPaymentMethod()`: Cho phép nhân viên chọn phương thức thanh toán mong muốn.
  + `updatePaymentMethod()`: Cập nhật thông tin phương thức thanh toán của nhân viên trong hệ thống.

---

#### Lớp Giao Diện Nhân Viên (EmployeeUI)
- **Mô Tả:** Đại diện cho giao diện người dùng nơi nhân viên tương tác với hệ thống.
- **Phương Thức:**
  + `requestPaymentMethod()`: Yêu cầu nhân viên chỉ định phương thức thanh toán mà họ muốn.
  + `displayPaymentOptions()`: Hiển thị danh sách các phương thức thanh toán có sẵn để nhân viên lựa chọn.
  + `getSelectedPaymentMethod()`: Lấy phương thức thanh toán mà nhân viên đã chọn sau khi họ đã thực hiện lựa chọn.
  + `displayConfirmation()`: Hiển thị thông báo xác nhận cho nhân viên sau khi họ đã chọn phương thức thanh toán.

---

#### Lớp Quản Lý Thanh Toán (PaymentController)
- **Mô Tả:** Chịu trách nhiệm quản lý các thao tác liên quan đến việc lựa chọn phương thức thanh toán.
- **Phương Thức:**
  + `getPaymentMethods()`: Trả về danh sách các phương thức thanh toán có sẵn mà nhân viên có thể chọn.
  + `processPaymentMethodSelection(method, address, bankName, accountNumber)`: Xử lý lựa chọn của nhân viên, kiểm tra tính hợp lệ và cập nhật thông tin vào lớp Nhân Viên.

### Giải Thích Mối Quan Hệ
- **Giao Diện Nhân Viên (EmployeeUI)** tương tác với **Quản Lý Thanh Toán (PaymentController)** để:
  + Lấy danh sách các phương thức thanh toán có sẵn thông qua `getPaymentMethods()`.
  + Gửi yêu cầu cập nhật thông tin phương thức thanh toán cho lớp Nhân Viên thông qua lớp Quản Lý Thanh Toán.

- **Quản Lý Thanh Toán (PaymentController)** cập nhật thông tin cho lớp Nhân Viên khi nhận được lựa chọn từ giao diện người dùng và xử lý logic nghiệp vụ.

