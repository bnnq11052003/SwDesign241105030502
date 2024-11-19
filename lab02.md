# Lab 2
## Nguyễn Văn Trường - 4451051021
## 1. Login

### Các lớp phân tích chính

#### Entity:

- **User**:  
    Là thực thể chứa thông tin về người dùng, bao gồm tên người dùng và mật khẩu.

#### Boundary:

- **LoginUI**:  
    Giao diện người dùng cho phép người dùng nhập thông tin đăng nhập.

#### Control:

- **LoginController**:  
    Điều khiển quy trình xác thực thông tin đăng nhập của người dùng.

## Biểu đồ Sequence cho Login

![Biểu đồ Sequence Login](https://www.planttext.com/api/plantuml/png/R94nRW8n44LxdsBA82KNs292eegKbWDCiBLhuHqJUvQ8CgACKd04H4r7jIueu28-GQuGEqisQ4bZUKR_pt-Z-Gh7iMTqtDH6u8ojWwbNJhpOXYIw5JpRKjFqISmiiREcgoTTOP9G4MjUTIQHNtXu_3KLG5LizmjeKf-mLlUmGE_Vh9FY8kdLVoCBA6FurB14eoMocZWbSmeQVtSxQ2G6zZmnSnGmrp6iQs27mDNfG2Mm9ZXlpklqxSWknFz1i8lj3fOnlCCyjaU6roOrRjEkrqtWUtqj7wJrI_UCLMQan1V3nq_aDcDMfwqUMCLOaSn7-WO00F__0m00)

## Biểu đồ lớp mô tả lớp phân tích và giải thích

![Biểu đồ lớp Login](@startuml
class User {
    - username: String
    - password: String
    + checkPassword(password: String): boolean
}

class LoginUI {
    + enterCredentials(username: String, password: String)
    + displayLoginStatus(status: boolean)
}

class LoginController {
    + validateCredentials(username: String, password: String)
}

User --> LoginController : sử dụng
LoginUI --> LoginController : gọi phương thức
@enduml
)

## Giải thích các lớp

### 1. **User**  
   - **Mục đích**: Đại diện cho người dùng trong hệ thống, chứa thông tin đăng nhập.
   - **Thuộc tính**:
     - `username`: Tên đăng nhập của người dùng.
     - `password`: Mật khẩu của người dùng.
   - **Phương thức**:
     - `checkPassword(password: String)`: Kiểm tra tính hợp lệ của mật khẩu nhập vào.

### 2. **LoginUI**  
   - **Mục đích**: Giao diện người dùng cho phép nhập tên đăng nhập và mật khẩu.
   - **Phương thức**:
     - `enterCredentials(username: String, password: String)`: Nhập thông tin đăng nhập.
     - `displayLoginStatus(status: boolean)`: Hiển thị trạng thái đăng nhập (thành công hoặc thất bại).

### 3. **LoginController**  
   - **Mục đích**: Điều khiển quy trình xác thực đăng nhập, kiểm tra thông tin đăng nhập qua lớp `User`.
   - **Phương thức**:
     - `validateCredentials(username: String, password: String)`: Xác thực thông tin đăng nhập từ `LoginUI`.
## 2. Create Employee

### Các lớp phân tích chính
#### Entity:

- **EmployeeReport**:  
    Là thực thể đại diện cho báo cáo của nhân viên, bao gồm các thông tin như tổng số giờ làm việc, số giờ nghỉ phép hoặc tổng thu nhập.

#### Boundary:

- **EmployeeReportUI**:  
    Là giao diện người dùng cho phép nhân viên tạo ra và xem các báo cáo cá nhân của họ.

#### Control:

- **EmployeeReportController**:  
    Chịu trách nhiệm điều phối quá trình tạo báo cáo cá nhân từ yêu cầu của người dùng.

## Biểu đồ Sequence của Quá trình Tạo Báo cáo Nhân viên

![Biểu đồ Sequence Create Employee Report](https://www.planttext.com/api/plantuml/png/Z9A_IWD14CRxUOef5SmBN241jR0LV83DtP1RsEmUuspWIh584Nm8jH04iRyjBEv9zWby1VUIgCTT4co6-RFpuvkF_GgVqpjHB7vXGENY6AyMbN4r4SoSjuNY-hTpGvLZkRs6t5bXPmQ3YstN40DPqJ9S1FYfSN8-WcPOjsyUyzYyUfJOF3cSjIdaku2sR9yj3DV6g3yP6SvZUDT7m71eTOpTm1urCWbhMkwwbqhKYTGLdU76nbIdb6pH9QS3F4wEYXMEpGikOxZ78eOFD3g6bV-NsBr-Re_lcLWwd6lbiEZ0-wpiOJ8iqwi7YrB6iEw9W6cwhlijtm000F__0m00)

## Biểu đồ lớp và Mô tả các Thành Phần

![Biểu đồ lớp Employee Report](https://www.planttext.com/api/plantuml/png/b58nQiD04EprYYqLi3uWWZ74ALoOG4mUS3ujHk6iEqvxnaT8dNUa284qwQKYXLzoByWNif8bss0BaoiMTdPsPXRkj_wPb2GikRMAf19b2VThexH7V4IZBS5B1FmIi6qx5IHIc0jpko2R5wiHF2oVKTAuPG6p6CPDjzomO_86K-ZfhHdZ33Lr15Xan_RcilPhT37RqwnB1w0D5ZqOiyf6vratolBIAE7tq_ZA6VtgWEETBiXgfT0UdAL53jwf__FMtkhih2GP3pkdu7TV3cIeFXrGgDurB7TS99TeSEjSaeN8EWzR5weFWYpKtw3oKB-v4xq9Psx-nXy0003__mC0)

## Giải thích Chi Tiết về Các Lớp

### 1. **EmployeeReport**  
   - **Chức năng**: Quản lý và lưu trữ các báo cáo cá nhân của nhân viên, bao gồm số giờ làm việc, tổng thu nhập và số ngày nghỉ phép.
   - **Thuộc tính**:
     - `reportData`: Dữ liệu báo cáo, được lưu trữ dưới dạng key-value.
   - **Phương thức**:
     - `retrieveReportData(type: String, startDate: Date, endDate: Date)`: Truy xuất dữ liệu báo cáo theo loại báo cáo và phạm vi thời gian (từ ngày đến ngày).

### 2. **EmployeeReportUI**  
   - **Chức năng**: Cung cấp giao diện để nhân viên có thể tự tạo và xem báo cáo cá nhân của họ.
   - **Phương thức**:
     - `openReportUI()`: Mở giao diện tạo báo cáo.
     - `displayReport(reportData: Map<String, Object>)`: Hiển thị báo cáo cá nhân cho nhân viên sau khi tạo xong.

### 3. **EmployeeReportController**  
   - **Chức năng**: Quản lý toàn bộ quá trình tạo báo cáo, từ việc nhận yêu cầu từ `EmployeeReportUI` cho đến việc truy xuất dữ liệu từ `EmployeeReport`.
   - **Phương thức**:
     - `createReport(type: String, startDate: Date, endDate: Date)`: Tạo báo cáo cho nhân viên dựa trên yêu cầu về loại báo cáo và thời gian cụ thể.

## 3. Run PayRoll

### Các lớp phân tích chính

### Entity:
- **Employee**: Lưu thông tin về nhân viên (ID, lương cơ bản).
- **Payroll**: Tính toán bảng lương dựa trên dữ liệu nhân viên.

### Boundary:
- **PayrollUI**: Giao diện hiển thị kết quả bảng lương.

### Control:
- **PayrollController**: Điều khiển quy trình tính lương cho nhân viên.

## Biểu đồ Sequence

![Biểu đồ Sequence Run Payroll](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9hRa5EVcLgAbTIVcbUIc9HfK90OcLHVavEg2TNSdvU2P094t66S7DIYxXIyqeoI-1AOLouMLmmbeAk7S8yAuNAmwjA5P8VxbeE93CUxbfOgP3qSDVYl7I5d6CRZYtCI-U2gqNIYB3MIY7zuUwrcSZ6b1nUcvU1hXsX0yaOAwXQx3Ogw6AtiAG8g5oXxE7kHeNiXxlsboWKbW85i5c4wbE8Gv6quF4fK2SilAmKCZ8VxcxEKoZ9UBYx6rqFbqDgNWeewW00003__mC0)

## Biểu đồ Lớp

![Biểu đồ lớp Run Payroll](https://www.planttext.com/api/plantuml/png/Z9B1IiD048RlUOevHZ0l4AGKh8SUH55yW4aon9NfRjYTBGJn4No8ua4G2fxRWuT0toDFu2kOrZK4Oy6z3Cpi_ttBi9_RZwaJjE8N7EMCpi75ec9J4y5Z1Dr9W49ZNgHmArRfCWmSCjewXPdn6TEX2M2fkq9B-i7CK30-IU4IgxFlz2bSPG-KooHwYeBp6cjhc8CI84VEFQDG6CGqeFt9-gVXRjux2kKgnZeCRiXvbjWUoZ73qgXYX3mtMlQLR8zMMeaQl7uGxRUR99Cn8OMwUVEGjvjN3zAizJtmxdstwbO-jWq8APJjzbc5Y9XcfI5hDo-w_9tl5d34t17MQk2FfgIB_RVu0W00__y30000)

## Giải Thích Các Thành Phần

- **Employee**: Lưu trữ thông tin nhân viên và mức lương cơ bản.
  - `retrieveEmployeeData()`: Lấy dữ liệu nhân viên.

- **Payroll**: Tính toán bảng lương cho nhân viên.
  - `calculatePayroll(employeeData)`: Tính lương từ dữ liệu nhân viên.

- **PayrollUI**: Hiển thị kết quả bảng lương.
  - `displayPayrollResult(result)`: Hiển thị bảng lương.

- **PayrollController**: Quản lý quy trình tính lương.
  - `initiatePayroll()`: Khởi động quá trình tính lương cho nhân viên.

## 4. Maintain Purchase Order

### Các lớp phân tích chính
### Entity:
- **PurchaseOrder**: Lưu trữ thông tin về đơn hàng của nhân viên có hoa hồng, bao gồm khách hàng, sản phẩm và ngày tạo đơn hàng.

### Boundary:
- **PurchaseOrderUI**: Giao diện cho nhân viên nhập liệu, tạo, cập nhật hoặc xóa đơn hàng.

### Control:
- **PurchaseOrderController**: Điều khiển các thao tác trên đơn hàng, đảm bảo rằng chỉ nhân viên có hoa hồng mới có quyền truy cập và chỉnh sửa.

## Biểu đồ Sequence

![Sequence Diagram](https://www.planttext.com/api/plantuml/png/Z9AnJiCm48PtFyMzGDKz0wfKCJ31mWEOn8gj9kVYd2iy8aOctg0H0rAbJcp9qC68z_0Jy0euwX2IfXMJpoVTztyw-wSzB2hYXcnPC9wIDh3KPQcgIcaKsNMvBhGJWZreYnat3kwiIIMlnAt9XBc_OQb6CheOzfV7PY4C4qYAHcECJMN0x6fCJy3vdOKqD1yMA3IrdiTwlmQKyQ3va__ayFNsNID8lyMSZUPFaBrO0dbezseG8Ba6ydKAPFmEpuDxoab00YiLsfSo8ZWyMXVQPuorTN0Kt_XjdpEamkoIBPdGlCCcyc0LcWD5UDSum_fhEBLMsKb6CHdQr__mkbL6pjIpZM2TPurvlFbQ3LR85WApxflz0W00__y30000)

## Biểu đồ Lớp

![Class Diagram](https://www.planttext.com/api/plantuml/png/b9DFIWCn5CRtSugt7C6vm22bqhheGYiK3n2JHoUIIORaHIZY8Ro1NGa5Bs0NBaQyHq_W5Pnfftyc8wLcaK1UlY-_z_Boi_piEsAMVAuYhfXpC31vBfsJHgEuoWjbPeZm544r4i1cOoHIc92LUje4DCknjGN0BJB2MszvnXoEhK0RcteUCc8fNBFYOdF-7CRt3yYfTvR2ev4YUeuQbfPu1x4swH1mxyZaQ6z2aWGAQuJdD4HYKhaWk4MgHFNSWZ-HToFnXVYlHA32hQHEI6ewNeExKLC505EW3c9nu2vTeTXi7PmG8-zYjrws5JX-ry1eiaQfNUMXufCamqUzv5GrItnWzcSB9Kalp2M5MRdmm5SVRnueOmQedFCepBYZt9EbC5qjt-K9FWVPTFpIlGZ8bWiDNo_VSmrP-LgrIH-rgB_7Bm000F__0m00)

## Giải thích các lớp

- **CommissionedEmployee**: Đại diện cho nhân viên hưởng hoa hồng, có quyền tạo và chỉnh sửa đơn hàng.
  - `createPurchaseOrder(orderData: Map<String, Object>)`: Tạo đơn hàng mới.

- **PurchaseOrder**: Lưu trữ thông tin đơn hàng.
  - `create(orderData: Map<String, Object>)`: Tạo đơn hàng mới.
  - `update(orderData: Map<String, Object>)`: Cập nhật đơn hàng.
  - `delete(orderId: int)`: Xóa đơn hàng.

- **PurchaseOrderUI**: Giao diện người dùng cho thao tác với đơn hàng.
  - `openPurchaseOrderUI()`: Mở giao diện tạo/hiệu chỉnh đơn hàng.
  - `displayOrderStatus(status: String)`: Hiển thị trạng thái đơn hàng.
 
## 5. Maintain Employee Information

### Các lớp phân tích chính
### Entity:

- **Employee**: Thực thể lưu thông tin của nhân viên, như loại nhân viên, mức lương, và các thông tin cá nhân.

### Boundary:

- **EmployeeInfoUI**: Giao diện cho quản trị viên để thêm, cập nhật hoặc xóa thông tin nhân viên.

### Control:

- **EmployeeInfoController**: Điều khiển quy trình quản lý thông tin nhân viên.

## Biểu đồ Sequence cho Maintain Employee Information  

![Diagram](https://www.planttext.com/api/plantuml/png/V94n3i8m34NtdC8Z3Br01rHK6BgnS00hSQL8YHq5C_Hi31o9Az1AI4shbj7sV__hov_NktaePdt6OD2gPBZXa2M4iukUJHfFtlg4h72DASX0r74lzsxtr0hhP41vKs9C6G3LQULRWoJYSdSucgLa3Ss9DQ1p2vP-mmKLbpupLVhLO3EXqWu8rPziAzpx756zy6xKHc7d7odWq1RusBaXTjDNlW000F__0m00)

---

## Các biểu đồ lớp mô tả lớp phân tích và giải thích  

![Diagram](https://www.planttext.com/api/plantuml/png/d991QiCm44NtEiKiNQWl84e8j5buKR9eSu29DIaguv6GnWLJUh8kUgHUeOxZW9qcXMQfcVy-yp_w_lnQPiMaRSF6r8mvmwg973eYU3S09T3uh9m5BphC11koyAJ9oyjCzDp5-I8ZO-eikD1kcVeHG9q8bOeZye2A5XuntXsmMrXlNwdMnOs5j-3TmBJH_Pjnn3HXnlkFYe_Jk9NimgOQGWE4I39T53DZdoDZTnzavrE3weCKVzhsIas1cT9eZyxDtA_eudh-qCjP_dT79-sKvU9ICWkRJDbSs4v1s9yeFhRSvyZ6B4dS_l_z0000__y30000)

## Giải thích các lớp

#### Employee

- **Mục đích**: Lưu trữ thông tin của từng nhân viên, cho phép quản trị viên thực hiện các thao tác thêm, sửa, xóa nhân viên.
- **Thuộc tính**:
    - `employeeId`: ID duy nhất của nhân viên.
    - `name`: Tên của nhân viên.
    - `employeeType`: Loại nhân viên (theo giờ, lương cố định, có hoa hồng).
    - `salary`: Mức lương của nhân viên.
- **Phương thức**:
    - `create(employeeData: Map<String, Object>)`: Tạo mới thông tin nhân viên.
    - `update(employeeData: Map<String, Object>)`: Cập nhật thông tin nhân viên.
    - `delete(employeeId: int)`: Xóa thông tin nhân viên.

#### EmployeeInfoUI

- **Mục đích**: Giao diện cho phép quản trị viên tương tác để thêm, sửa hoặc xóa thông tin nhân viên.
- **Phương thức**:
    - `openEmployeeInfo()`: Mở giao diện thông tin nhân viên.
    - `displayConfirmation()`: Hiển thị kết quả sau khi thực hiện thao tác.

#### EmployeeInfoController

- **Mục đích**: Điều khiển quá trình quản lý thông tin nhân viên, đảm bảo các thay đổi từ `EmployeeInfoUI` được thực hiện thông qua `Employee`.
- **Phương thức**:
    - `addEmployeeInfo(employeeData: Map<String, Object>)`: Thêm mới thông tin nhân viên.
    - `updateEmployeeInfo(employeeData: Map<String, Object>)`: Cập nhật thông tin nhân viên.
    - `deleteEmployeeInfo(employeeId: int)`: Xóa thông tin nhân viên.
 
## 6. Create Administrative Report

### Các lớp phân tích chính
### Entity:
- **Employee**: Lưu thông tin của từng nhân viên để tạo báo cáo.
  
-  **AdministrativeReport**: Thực thể báo cáo quản trị lưu các dữ liệu như tổng số giờ làm việc hoặc tổng lương đến thời điểm hiện tại.
### Boundary:

- **AdminReportUI**: Giao diện cho phép quản trị viên nhập thông tin để tạo báo cáo.

### Control:

- **AdminReportController**: Điều khiển quá trình tạo báo cáo quản trị từ thông tin nhập vào của quản trị viên.

## Biểu đồ Sequence cho Create Administrative Report 

![Diagram](https://www.planttext.com/api/plantuml/png/X99DZi8m38NtEKMM834Nc0K2CKWpsv56hAtMWcZI979SKC_6WYDn1LoIKihlhedV-_pizBW_p283SLrP1GLxqlEoCau5kJE52U0utVnYyCH_Fyyg2--OlBL80yMo2jOtYFSs4vc0pHQJNwdphVwO3llfJ-q3NewZiHgMExteq35IAdm1GoUzGVP1nL8G0kS4e_CYn8aJGPNjnw3PbL68tM028MGokCMLf_zlNrDyIBeONiGHKarExmIaDotfUVz7EnJ26XrIFr9FckW85gZ98zqwtuUY92nbiszINJrTQMAmqEGq2V7Y1RCyzr8pMLxxOvu0003__mC0)

---

## Các biểu đồ lớp mô tả lớp phân tích và giải thích

![Diagram](https://www.planttext.com/api/plantuml/png/X9B1QW8n48RlUOevhk2-G2XYQGlr80MBU4utWwJD9c4oBaZnoJpqaVeApRenegZD8J2J-VDDvi_l_cSQMH5lMYiQgsA4bpPOlqM4Rm5frO0vCTCItfcCM-S3freyIm4GfWWxN7dwUlKRYjNXzcV5gRBVnu1EdyAH1EDOx4I6F-hME1EP59iE5nWySMc43c6IAGbp5Hu6yXZUFZwnuKbkOOqEapoBAtshFA4xR_G5Ur0jPnaAu0EMP7NK34VQn63LDeE6xkJL9znZFNd7vAr5Aio6yFI0VmTulBaOLzUJ6m1P389-Bk9wLT5V6Y7BSBCNudnczy39vgHiM4nJ__rl-mC00F__0m00)

## Giải thích các lớp
#### Employee

- **Mục đích**: Đại diện cho thông tin cơ bản của nhân viên trong hệ thống, phục vụ việc tổng hợp dữ liệu tạo báo cáo.
- **Thuộc tính**:
    - `employeeId`: Mã định danh duy nhất của mỗi nhân viên.
    - `name`: Tên của nhân viên.
- **Phương thức**:
    - `retrieveWorkHours(startDate: Date, endDate: Date)`: Trả về số giờ làm việc của nhân viên trong khoảng thời gian nhất định.

#### AdministrativeReport

- **Mục đích**: Đại diện cho báo cáo quản trị tổng hợp thông tin về tổng giờ làm việc hoặc tổng thu nhập của nhân viên.
- **Thuộc tính**:
    - `reportData`: Dữ liệu báo cáo, lưu dưới dạng key-value chứa thông tin chi tiết về báo cáo.
- **Phương thức**:
    - `generateReport(data: Map<String, Object>)`: Tạo báo cáo dựa trên dữ liệu được cung cấp từ lớp `Employee`.

#### AdminReportUI

- **Mục đích**: Giao diện người dùng cho phép quản trị viên tương tác, tạo và xem báo cáo.
- **Phương thức**:
    - `openReportUI()`: Mở giao diện báo cáo.
    - `displayReport(report: AdministrativeReport)`: Hiển thị báo cáo sau khi được tạo.

#### AdminReportController

- **Mục đích**: Điều khiển quá trình tạo báo cáo quản trị, nhận yêu cầu từ AdminReportUI và lấy dữ liệu từ Employee.
- **Phương thức**:
    - `createReport(startDate: Date, endDate: Date)`: Tạo báo cáo trong khoảng thời gian nhất định, tổng hợp dữ liệu và hiển thị báo cáo.


## 7. Code Java mô phỏng ca sử dụng Maintain Timecard

import java.util.HashMap;
import java.util.Map;

class Timecard {

    private Map<String, Integer> hoursWorked = new HashMap<>();
    private boolean submitted = false;

    public void addHours(String date, int hours) throws Exception {
        if (submitted) {
            throw new Exception("Timecard đã được gửi, không thể chỉnh sửa.");
        }
        if (hours < 0 || hours > 24) {
            throw new IllegalArgumentException("Số giờ phải trong khoảng 0 - 24.");
        }
        hoursWorked.put(date, hours);
    }

    public void submit() {
        if (!submitted) {
            submitted = true;
            System.out.println("Timecard đã được gửi.");
        }
    }

    public void display() {
        System.out.println("Chi tiết Timecard:");
        hoursWorked.forEach((date, hours) -> System.out.println("Ngày: " + date + ", Giờ làm: " + hours));
        System.out.println("Trạng thái: " + (submitted ? "Đã gửi" : "Chưa gửi"));
    }

}

public class Main {

    public static void main(String[] args) {
        try {
            Timecard timecard = new Timecard();
            timecard.addHours("2024-11-01", 8);
            timecard.addHours("2024-11-02", 6);
            timecard.display();
            timecard.submit();
            timecard.display();
            timecard.addHours("2024-11-03", 5);
        } catch (Exception e) {
            System.out.println("Lỗi: " + e.getMessage());
        }
    }

}
