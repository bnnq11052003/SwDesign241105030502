
## Họ tên: Nguyễn Văn Trường
## Mã sinh viên: 4451051021

## Bảng thiết kế các lớp trong từng hệ thống con
**I. Timecard Management Subsystem**

### **TimecardForm (Boundary)**
- **Thuộc tính**:
  - `timecardData`
- **Phương thức**:
  - `inputTimecard()`: Nhập dữ liệu bảng chấm công.
  - `displayTimecard()`: Hiển thị thông tin bảng chấm công.

---

### **TimecardController (Control)**
- **Thuộc tính**:
  - `timecardDatabase`
- **Phương thức**:
  - `getTimecard(employeeId)`: Lấy bảng chấm công theo mã nhân viên.
  - `saveTimecard(timecard)`: Lưu thông tin bảng chấm công.

---

### **Timecard (Entity)**
- **Thuộc tính**:
  - `employeeId`, `date`, `hoursWorked`, `projectCode`

---

### **ProjectManagementDatabase (Subsystem)**
- **Phương thức**:
  - `getProjectCode(projectName)`: Lấy mã dự án từ tên dự án.

---

## 2. Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/T95DRi9038NtESKiOP4BiAYGg2frGSMYKjScyqH3voVO7YI4Uh8kUgHUeUaa8HI5tSopt-Sd--VhUobAhCcxed8aObvhZuhOFaNsvbmOKnhjfKTIQWLZwj0a7HfdywpPMXf7folrixX1hc9GZiw19y1R4cJG3YCQld7n13pRReZG4PVYu9wOrFD7U_vQKkJ7UqmiRv4_q1KQZdjKkeeM8slJYMiAj8D7q25bXkUScz4twnalv943_TjZMJvCRM7HRbB1LAaK4-LhLzkR17VRxeTTc4C2rwrrYM3_xlmB003__mC0)

**II. Payroll Processing Subsystem**

### **PayrollController (Control)**
- **Thuộc tính**:
  - `employeeData`: Dữ liệu về nhân viên.
  - `payrollDatabase`: Cơ sở dữ liệu quản lý thông tin tiền lương.
- **Phương thức**:
  - `calculateSalary(employeeId)`: Tính toán tiền lương cho nhân viên dựa vào mã nhân viên.
  - `processPayroll(employeeId)`: Xử lý thanh toán lương cho nhân viên.

---

### **Employee (Entity)**
- **Thuộc tính**:
  - `employeeId`: Mã định danh của nhân viên.
  - `name`: Tên của nhân viên.
  - `salaryType`: Loại hình lương (theo giờ, theo tháng...).
  - `bankDetails`: Thông tin tài khoản ngân hàng của nhân viên.

---

### **Paycheck (Entity)**
- **Thuộc tính**:
  - `employeeId`: Mã nhân viên nhận lương.
  - `amount`: Số tiền thanh toán.
  - `paymentDate`: Ngày thanh toán.
  - `status`: Trạng thái thanh toán (đã thanh toán, chưa thanh toán...).

---

### **SystemClockInterface (Boundary)**
- **Phương thức**:
  - `getCurrentDateTime()`: Lấy ngày và giờ hiện tại từ hệ thống.

---

### **BankSystem (Subsystem)**
- **Phương thức**:
  - `processPayment(employee, amount)`: Xử lý thanh toán lương qua ngân hàng cho nhân viên với số tiền cụ thể.

---

## Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/T5AzJiCm4Dxp53SMYOWz0wf86ReXjIzmTGw8uf_WEmyHuiaOU2HU0Jjncm3DPD_vlhzBlZ-_jYpe9HXTA8tCy8I3TrhNpaewoSDx0L02cLwxWMY7WcEZdmPJVKAcs0DGg5NGA7H0ZNxOd47xvcPyxxrJn9mrVZr_5Dd0Osx-qTqtOsdHq7ZXKU4uz5DvGjljIB3LF5D57VLAghjEXSO5A-SiXgp4B9bSKCA2w32maAcrKztU2lbdL9C_W1UIEdYVqSVMq6OHvY7Qci1vVDv04hniu3Qx6Q7_Fq5PtizxgG1LuY1UcRp4ha1vYgxuBlHDEbS0L-DLy1R8jwkWHRGAc6p3u2b2MBZOnZBzKZy0003__mC0)

**III. Authentication Subsystem**

### **LoginForm (Boundary)**
- **Thuộc tính**:
  - `username`: Tên đăng nhập do người dùng nhập vào.
  - `password`: Mật khẩu do người dùng cung cấp.
- **Phương thức**:
  - `submitLogin()`: Gửi thông tin đăng nhập (username và password) để xác thực.
  - `displayErrorMessage()`: Hiển thị thông báo lỗi nếu đăng nhập thất bại.

---

### **AuthenticationSystem (Control)**
- **Thuộc tính**:
  - `userDatabase`: Đối tượng chứa dữ liệu về người dùng.
- **Phương thức**:
  - `authenticate(username, password)`: Kiểm tra thông tin đăng nhập, đối chiếu với cơ sở dữ liệu.
  - `manageSession(user)`: Quản lý phiên đăng nhập sau khi xác thực thành công.

---

### **UserDatabase (Entity)**
- **Thuộc tính**:
  - `users`: Danh sách người dùng, bao gồm thông tin như tên đăng nhập, mật khẩu (được mã hóa), vai trò, v.v.
- **Phương thức**:
  - `findUser(username)`: Tìm kiếm người dùng theo tên đăng nhập.
  - `validatePassword(user, password)`: Xác minh mật khẩu do người dùng cung cấp với mật khẩu đã lưu trữ.

---

## Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/T95DJWCn38NtSmelMucvm2nGaO0LI4WL1t0RJx6KdpREK5M8ax7WI5m19pFj1Aai7J-_xyN--VfUISAO1cURhKKHU0exzeyXElXe05eOXA97HwNOg-8Oej42G8QDurJqYsLvCInxYwU764Dy9X7SaNO-cydwRaXlv1DlCN7mwvCagYdtc723GiKAPoqjpXbkBW56daElYBMIrA-eAjfhPLbHf4psx4qMNAn7mtUqR9JuCc5AkwQg-xoWjhsz_gTkses0pM8mb92jD5V5sULFrWuE0qKcWJx4aXaq4_u_FIVgpYSGe7m4SECL1BYlLwhpq9T8A_8c7_yN003__mC0)

**IV. Bank Interaction Subsystem**

### **IBankSystem (Interface)**
- **Phương thức**:
  - `transferFunds(employeeBankInfo, amount)`: Phương thức này được sử dụng để thực hiện chuyển tiền từ tài khoản ngân hàng của nhân viên sang tài khoản đích. Cần cung cấp thông tin tài khoản ngân hàng của nhân viên và số tiền cần chuyển.

---

### **BankSystem (Implementation)**
- **Mô tả**: Lớp này triển khai giao diện `IBankSystem`. Nó thực hiện các phương thức cụ thể để tương tác với API của ngân hàng, như chuyển tiền và kiểm tra trạng thái giao dịch.
- **Phương thức**:
  - `transferFunds(employeeBankInfo, amount)`: Phương thức này sử dụng thông tin tài khoản ngân hàng của nhân viên và thực hiện việc chuyển tiền thực tế qua API ngân hàng.

---

### **BankInformation (Entity)**
- **Thuộc tính**:
  - `bankName`: Tên của ngân hàng nơi tài khoản được mở.
  - `accountNumber`: Số tài khoản ngân hàng của nhân viên.
  - `routingNumber`: Mã số định tuyến ngân hàng giúp xác định ngân hàng khi thực hiện giao dịch.

---

## Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/h90n3i8m34NtdC8ZIEG22A6A0QbB5qxWfYwAQ1mKEqC5d8o18t45cegX4YlU_6n_V_lzV5MYc3I7mNXMIZqwWlg0V3cDeXJWPc0AJSZIKpfcxcH5uJh4aQYqrTp73M28cNLj7iQu0KNWFmgbb0AgZppBM6Wdsc2WEK7dob2JGqjf9YbczNp-aabhUShkRktIs1RyP8C2iOfPS6ltFzkta8N4c8guAy_w0000__y30000)

**V. Printing Subsystem**
### **IPrintService (Interface)**
- **Mô tả**: Giao diện `IPrintService` xác định các phương thức cơ bản để dịch vụ in ấn thực hiện việc in tài liệu. Mọi lớp triển khai giao diện này sẽ phải cung cấp cách thức thực hiện phương thức `printDocument()` để xử lý việc in ấn các tài liệu.
- **Phương thức**:
  - `printDocument(documentData)`: Phương thức này nhận đầu vào là dữ liệu tài liệu (`documentData`) và thực hiện in tài liệu đó.

---

### **PrintService (Implementation)**
- **Mô tả**: Lớp `PrintService` là lớp thực thi giao diện `IPrintService`. Lớp này cung cấp phương thức `printDocument()` để thực hiện in tài liệu dựa trên dữ liệu nhận được. Đây có thể là việc gửi tài liệu đến một máy in vật lý hoặc lưu trữ tài liệu dưới dạng PDF, tùy thuộc vào yêu cầu hệ thống.
- **Phương thức**:
  - `printDocument(documentData)`: Phương thức này nhận dữ liệu tài liệu cần in và thực hiện thao tác in (có thể là in vật lý hoặc tạo tài liệu PDF).

---

### **Paycheck (Entity)**
- **Mô tả**: Lớp `Paycheck` được sử dụng trong `Payroll Processing Subsystem`. Đây là đối tượng đại diện cho một bảng lương đã được tính toán và có thể được in ra dưới dạng tài liệu. Dữ liệu của `Paycheck` sẽ bao gồm các thông tin như số tiền, ngày thanh toán, trạng thái thanh toán, v.v.
- **Thuộc tính**:
  - `employeeId`: Mã nhân viên.
  - `amount`: Số tiền thanh toán.
  - `paymentDate`: Ngày thanh toán.
  - `status`: Trạng thái của thanh toán (ví dụ: Đã thanh toán, Chờ xử lý).
  
---
## Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/d90n3i8m34Ltdo8Z3Bb0XL27BjsGE86L6b6Hf5Ni84N0oHWu4bSW2PLGLppzR-j_FVdzVBKi62Gw2wCN2YSqfFf3oEP8uJfcTmELPowhRZBHaPVDi8WE1RVm030McTNVEKpcJEPICrgHc-sKYFgXMdHJz5BbZ6c9K_KPNYANeZNpxgxrcgPHOswbacPONRJU_m2QBp03jEI7yfOF0000__y30000)

**VI. Project Management Subsystem**

### **IProjectManagementDatabase (Interface)**
- **Mô tả**: Giao diện `IProjectManagementDatabase` định nghĩa các phương thức cơ bản để hệ thống quản lý dự án có thể truy xuất các mã dự án. Lớp triển khai giao diện này sẽ thực hiện các phương thức để tương tác với cơ sở dữ liệu hoặc các hệ thống lưu trữ dữ liệu.
- **Phương thức**:
  - `getProjectCodes()`: Phương thức này trả về danh sách các mã dự án. Có thể là một danh sách các mã dự án hiện có trong hệ thống.

---

### **ProjectManagementDatabase (Implementation)**
- **Mô tả**: Lớp `ProjectManagementDatabase` là lớp thực thi giao diện `IProjectManagementDatabase`. Lớp này cung cấp phương thức `getProjectCodes()` để truy xuất các mã dự án từ cơ sở dữ liệu hoặc hệ thống quản lý dự án.
- **Phương thức**:
  - `getProjectCodes()`: Phương thức này lấy danh sách mã dự án từ cơ sở dữ liệu hoặc một nguồn lưu trữ dữ liệu. Các mã dự án này sẽ được trả về dưới dạng một danh sách hoặc một cấu trúc dữ liệu khác.

---

## Sơ Đồ UML
![Diagram](https://www.planttext.com/api/plantuml/png/d90n2W8n44NxEKLABNA1HMIBRROJFC6GZ1XCiaio4O9wCWkFv1NCnWL9wrJ_p_0_Zta_Ntra39oS1UEPmWaLYV4GYZbIk9hYRY3ApCjgc5Hov7cZLp4WunOU0CfYZEBl76Pr9dMf6Id8pNRAHAEk5jsKF5SvOrxZL7s1vnINefPvTvUofUc4AQsqf2Cq5odtFu3k2nm1UlAwlEK3003__mC0)
