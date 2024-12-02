## Họ tên: Nguyễn Văn Trường
## Mã sinh viên: 4451051021

# Thiết Kế Hệ Thống Con Cho Ca Sử Dụng TimeCard

## 1. Phân Phối Hành Vi Của Hệ Thống Con Đến Các Phần Tử

### Thành Phần Hệ Thống Con

#### a) **TimecardForm**
- **Chức năng**:  
  Giao diện người dùng cho phép nhập và hiển thị thông tin thời gian làm việc của nhân viên.

- **Phương thức**:  
  - **displayTimecard()**: Hiển thị thông tin thời gian làm việc hiện tại.  
  - **saveTimecard()**: Lưu thông tin giờ làm việc từ nhân viên vào hệ thống.  

---

#### b) **TimecardController**
- **Chức năng**:  
  Điều khiển và xử lý các yêu cầu từ **TimecardForm**, thực hiện các nghiệp vụ liên quan đến việc quản lý thời gian làm việc.

- **Phương thức**:  
  - **getChargeCodes()**: Lấy mã chi phí cho các yêu cầu nhập giờ làm việc.  
  - **getCurrentTimecard()**: Trả về thông tin về thời gian làm việc hiện tại của nhân viên.  
  - **updateTimecard()**: Cập nhật thông tin giờ làm việc trong hệ thống.  

---

#### c) **ProjectManagementDatabase**
- **Chức năng**:  
  Lưu trữ thông tin về thời gian làm việc của nhân viên, liên kết với các mã dự án tương ứng.

- **Phương thức**:  
  - **saveTimecard()**: Lưu thông tin thời gian làm việc vào cơ sở dữ liệu.  

---

#### d) **Timecard**
- **Chức năng**:  
  Đối tượng đại diện cho thông tin về thời gian làm việc của nhân viên.

- **Thuộc tính**:  
  - **date**: Ngày làm việc.  
  - **hours**: Số giờ làm việc trong ngày.  

---

## 2. Tài Liệu Hóa Các Phần Tử Của Hệ Thống Con

### Các Thành Phần Và Phương Thức

#### a) **TimecardForm**
- **Chức năng**:  
  Cung cấp giao diện người dùng để nhập và hiển thị thông tin về giờ làm việc.

- **Phương thức**:
  - **displayTimecard()**:  
    Mô tả: Hiển thị thông tin giờ làm việc hiện tại.  
    Tham số: Không có.  
    Trả về: Không có, chỉ hiển thị dữ liệu trên giao diện.

  - **saveTimecard()**:  
    Mô tả: Lưu thông tin giờ làm việc từ người dùng vào hệ thống.  
    Tham số: Thông tin giờ làm việc (ngày và số giờ làm).  
    Trả về: Xác nhận việc lưu dữ liệu thành công hoặc thất bại.

---

#### b) **TimecardController**
- **Chức năng**:  
  Điều khiển và xử lý logic nghiệp vụ cho hệ thống thời gian làm việc, bao gồm việc cập nhật và lấy thông tin giờ làm.

- **Phương thức**:
  - **getChargeCodes()**:  
    Mô tả: Lấy mã chi phí liên quan để nhập số giờ làm việc.  
    Tham số: Không có.  
    Trả về: Mảng mã chi phí (charge codes).

  - **getCurrentTimecard()**:  
    Mô tả: Trả về thông tin về thời gian làm việc của nhân viên trong ngày hiện tại.  
    Tham số: Không có.  
    Trả về: Đối tượng **Timecard** chứa thông tin về ngày và số giờ làm việc.

  - **updateTimecard()**:  
    Mô tả: Cập nhật thông tin giờ làm việc của nhân viên.  
    Tham số: Đối tượng **Timecard** mới với thông tin cập nhật.  
    Trả về: Xác nhận việc cập nhật thành công hoặc thất bại.

---

#### c) **ProjectManagementDatabase**
- **Chức năng**:  
  Cung cấp chức năng lưu trữ và truy xuất thông tin thời gian làm việc của nhân viên.

- **Phương thức**:
  - **saveTimecard()**:  
    Mô tả: Lưu thông tin giờ làm việc vào cơ sở dữ liệu.  
    Tham số: Đối tượng **Timecard** chứa dữ liệu giờ làm việc.  
    Trả về: Xác nhận việc lưu trữ thành công hoặc thất bại.

---

#### d) **Timecard**
- **Chức năng**:  
  Đối tượng đại diện cho thông tin về giờ làm việc của nhân viên.

- **Thuộc tính**:
  - **date**:  
    Mô tả: Ngày làm việc của nhân viên.  
    Kiểu dữ liệu: **Date**.
  
  - **hours**:  
    Mô tả: Số giờ làm việc của nhân viên trong ngày.  
    Kiểu dữ liệu: **Integer**.

- **Phương thức**:
  - **getDate()**:  
    Mô tả: Lấy ngày làm việc của nhân viên.  
    Tham số: Không có.  
    Trả về: **Date**.

  - **getHours()**:  
    Mô tả: Lấy số giờ làm việc của nhân viên.  
    Tham số: Không có.  
    Trả về: **Integer**.

  - **setDate(date)**:  
    Mô tả: Cập nhật ngày làm việc cho nhân viên.  
    Tham số: **Date** mới.  
    Trả về: Không có.

  - **setHours(hours)**:  
    Mô tả: Cập nhật số giờ làm việc cho nhân viên.  
    Tham số: **Integer** mới.  
    Trả về: Không có.


---

## 3. Mô Tả Các Phụ Thuộc Của Hệ Thống Con

### Mối Quan Hệ Giữa Các Thành Phần Trong Hệ Thống Con TimeCard

#### a) **Nhân viên (Employee)**
- **Vai trò**:  
  Nhân viên là tác nhân tương tác với hệ thống. Họ nhập thông tin thời gian làm việc thông qua **TimecardForm**.
- **Phụ thuộc**:  
  Cần cung cấp thông tin cá nhân và thông tin mã dự án từ hệ thống quản lý nhân sự và dự án để nhập liệu chính xác.

---

#### b) **TimecardForm**
- **Vai trò**:  
  Là giao diện người dùng, giúp nhân viên nhập liệu và hiển thị thông tin thời gian làm việc.
- **Phụ thuộc**:  
  - Phụ thuộc vào **TimecardController** để xử lý logic và cập nhật dữ liệu.
  - Dữ liệu nhập từ người dùng được gửi đến **ProjectManagementDatabase** thông qua **TimecardController**.

---

#### c) **TimecardController**
- **Vai trò**:  
  Điều khiển nghiệp vụ, xử lý logic giữa giao diện và cơ sở dữ liệu. 
- **Phụ thuộc**:  
  - Nhận dữ liệu từ **TimecardForm** để xử lý các yêu cầu.
  - Gửi và nhận thông tin từ **ProjectManagementDatabase** để lưu trữ hoặc truy vấn dữ liệu thời gian làm việc.
  - Dựa vào mã chi phí (charge codes) từ **ProjectManagementDatabase** để xác định dự án mà giờ làm việc được ghi nhận.

---

#### d) **ProjectManagementDatabase**
- **Vai trò**:  
  Lưu trữ thông tin liên quan đến thời gian làm việc của nhân viên và các mã dự án liên quan.
- **Phụ thuộc**:  
  - Phụ thuộc vào **TimecardController** để nhận dữ liệu cần lưu trữ.
  - Cung cấp mã chi phí (charge codes) và thông tin dự án khi được yêu cầu.

---

#### e) **Timecard**
- **Vai trò**:  
  Là đối tượng đại diện cho thông tin thời gian làm việc của nhân viên.
- **Phụ thuộc**:  
  - Được tạo ra hoặc cập nhật bởi **TimecardController** khi dữ liệu mới được nhập.
  - Được lưu trữ vào **ProjectManagementDatabase** để đảm bảo tính toàn vẹn dữ liệu.

---

### Tổng Quan Các Phụ Thuộc
- **Nhân viên** ➡ **TimecardForm**: Nhập liệu.
- **TimecardForm** ➡ **TimecardController**: Xử lý logic nhập liệu.
- **TimecardController** ➡ **ProjectManagementDatabase**: Lưu trữ dữ liệu thời gian làm việc.
- **TimecardController** ↔ **ProjectManagementDatabase**: Truy xuất mã chi phí (charge codes).
- **ProjectManagementDatabase** ➡ **Timecard**: Lưu trữ thông tin giờ làm việc.

Mối quan hệ trên giúp đảm bảo hệ thống con TimeCard hoạt động nhất quán, từ việc nhập dữ liệu đến lưu trữ và truy xuất thông tin.

---

## 4. Kiểm Tra (Checkpoints)

### Quy Trình Kiểm Tra Và Đánh Giá

1. **Xem xét thiết kế hệ thống**:  
   - Tổ chức các buổi họp định kỳ với các bên liên quan (nhà phân tích nghiệp vụ, lập trình viên, kiểm thử viên) để đánh giá chi tiết từng phần thiết kế.  
   - Đảm bảo các yêu cầu nghiệp vụ và kỹ thuật đã được phản ánh đầy đủ trong thiết kế.  
   - Thực hiện rà soát chéo (peer review) giữa các thành viên trong nhóm phát triển để xác minh tính chính xác và sự phù hợp của thiết kế.

2. **Kiểm thử đơn vị (Unit Testing)**:  
   - Xây dựng các kịch bản kiểm thử chi tiết cho từng thành phần:  
     - **TimecardForm**: Đảm bảo giao diện hiển thị đúng dữ liệu và thực hiện lưu thông tin chính xác.  
     - **TimecardController**: Đảm bảo logic nghiệp vụ được thực thi đúng theo yêu cầu, bao gồm việc lấy mã chi phí và cập nhật giờ làm việc.  
     - **ProjectManagementDatabase**: Xác minh dữ liệu thời gian làm việc được lưu trữ chính xác.  
   - Thực hiện kiểm thử từng phương thức để đảm bảo chúng hoạt động đúng với các trường hợp đầu vào khác nhau.

3. **Kiểm thử tích hợp (Integration Testing)**:  
   - Kiểm tra sự tương tác giữa các thành phần của hệ thống con (TimecardForm, TimecardController, ProjectManagementDatabase).  
   - Đảm bảo dữ liệu được truyền tải và xử lý chính xác giữa các thành phần.

4. **Đánh giá hiệu suất**:  
   - Đo lường thời gian xử lý khi lưu thông tin giờ làm việc vào cơ sở dữ liệu.  
   - Xác minh rằng hệ thống có thể xử lý đồng thời nhiều yêu cầu mà không ảnh hưởng đến hiệu năng.

5. **Phản hồi và cải tiến**:  
   - Ghi nhận các ý kiến phản hồi từ người dùng hoặc các bên liên quan sau khi thử nghiệm.  
   - Cập nhật và cải tiến thiết kế hoặc chức năng nếu phát hiện lỗi hoặc khả năng cải thiện.


