## Họ tên: Nguyễn Văn Trường
## Mã sinh viên: 4451051021
# Thiết kế hệ thống con của hệ thống tính lương

# 1. Phân Phối Hành Vi Của Hệ Thống Con Đến Các Phần Tử

Trong kiến trúc hệ thống, các hệ thống con được thiết kế để đảm nhận những chức năng riêng biệt, với các phần tử cụ thể thực hiện từng nhiệm vụ chi tiết. Phân phối hành vi như sau:

## a) Scheduler Subsystem

- **Chức năng**:  
  Scheduler Subsystem đảm nhận vai trò quản lý lịch trình và tự động kích hoạt các quy trình tính lương theo thời gian đã định. Hệ thống này đảm bảo rằng các quy trình quan trọng được thực thi một cách chính xác và đúng thời điểm, giảm thiểu sự phụ thuộc vào can thiệp thủ công.  

- **Các thành phần**:  
  - **SystemClock**: Thành phần này hoạt động như một công cụ theo dõi thời gian, chịu trách nhiệm kiểm tra và kích hoạt các quy trình như Run Payroll đúng lịch trình đã định.  
  - **ProjectManagementDatabase**: Thành phần này lưu trữ danh sách các mã dự án có liên quan, cung cấp dữ liệu cần thiết cho các quy trình sử dụng thông tin dự án.  

---

## b) Payroll Processing Subsystem

- **Chức năng**:  
  Payroll Processing Subsystem chịu trách nhiệm tính toán lương và thực hiện xử lý thanh toán. Đây là một trong những hệ thống quan trọng nhất trong kiến trúc, đảm bảo tính chính xác và bảo mật cho quy trình trả lương nhân viên.  

- **Các thành phần**:  
  - **PayrollController**: Thành phần chịu trách nhiệm xử lý toàn bộ logic nghiệp vụ liên quan đến tính toán lương, đảm bảo rằng mọi dữ liệu được tính toán đúng theo quy định.  
  - **BankSystemProxy**: Giao diện giữa hệ thống và ngân hàng, hỗ trợ chuyển khoản lương cho nhân viên một cách an toàn.  
  - **PrinterServiceProxy**: Công cụ hỗ trợ in phiếu lương, đảm bảo thông tin lương được hiển thị rõ ràng và đầy đủ.  
  - **PayrollDatabase**: Lưu trữ dữ liệu lương của nhân viên, đảm bảo rằng mọi thông tin được lưu giữ lâu dài và có thể truy cập khi cần.  

---

## c) Timecard Subsystem

- **Chức năng**:  
  Timecard Subsystem được thiết kế để theo dõi giờ làm việc của nhân viên và quản lý trạng thái thẻ chấm công. Hệ thống này đảm bảo rằng mọi thông tin liên quan đến giờ làm việc được cập nhật kịp thời và chính xác.  

- **Các thành phần**:  
  - **TimecardController**: Thành phần xử lý các nghiệp vụ liên quan đến việc quản lý thẻ chấm công, từ việc cập nhật giờ làm việc đến trạng thái sử dụng của thẻ.  
  - **TimecardForm**: Giao diện nhập liệu, cho phép người dùng nhập thông tin giờ làm việc và trạng thái thẻ một cách dễ dàng và trực quan.  

---

## d) Employee Management Subsystem

- **Chức năng**:  
  Employee Management Subsystem chịu trách nhiệm quản lý thông tin chi tiết về nhân viên và trạng thái làm việc của họ. Hệ thống này là nguồn cung cấp dữ liệu quan trọng cho các hệ thống con khác như Payroll Processing và Timecard Subsystem.  

- **Các thành phần**:  
  - **Employee**: Thực thể đại diện cho thông tin nhân viên, bao gồm các thuộc tính như họ tên, mã nhân viên, và trạng thái làm việc.  
  - **EmployeeDatabase**: Cơ sở dữ liệu lưu trữ thông tin chi tiết của nhân viên, từ dữ liệu cá nhân đến lịch sử làm việc.  

---

# 2. Phân Phối Hành Vi Của Hệ Thống Con Đến Các Phần Tử

## Scheduler Subsystem

- Hệ thống đảm bảo tự động kích hoạt quy trình tính lương theo lịch trình đã được định trước.  
- Quản lý và điều khiển việc thực thi các tác vụ quan trọng trong Payroll Processing Subsystem, đảm bảo quy trình tính lương luôn diễn ra đúng thời điểm mà không cần sự can thiệp thủ công.  

---

## Payroll Processing Subsystem

- Tính toán lương cho từng nhân viên dựa trên thông tin về giờ làm việc và trạng thái của nhân viên được cung cấp bởi các hệ thống liên quan.  
- Thực hiện thanh toán qua ngân hàng một cách an toàn, đồng thời cung cấp hỗ trợ in phiếu lương khi cần.  
- Lưu trữ dữ liệu lương nhân viên vào PayrollDatabase, đảm bảo thông tin được quản lý lâu dài và sẵn sàng để truy xuất khi cần thiết.  

---

## Timecard Subsystem

- Chịu trách nhiệm theo dõi và quản lý thông tin về giờ làm việc của nhân viên, bao gồm cả trạng thái của thẻ chấm công.  
- Sử dụng dữ liệu từ ProjectManagementDatabase để liên kết giờ làm việc với các dự án cụ thể, đảm bảo thông tin chính xác và dễ dàng đối chiếu.  
- Thường xuyên cập nhật trạng thái của thẻ chấm công trong hệ thống, đảm bảo mọi thông tin đều phản ánh chính xác thời điểm thực tế.  

---

## Employee Management Subsystem

- Hệ thống lưu trữ và quản lý toàn bộ thông tin chi tiết về nhân viên, từ dữ liệu cá nhân đến trạng thái làm việc hiện tại.  
- Cho phép thay đổi trạng thái nhân viên như đang làm việc, nghỉ việc hoặc bị xóa, đảm bảo hệ thống luôn phản ánh đúng tình trạng nhân sự.  
- Cung cấp dữ liệu liên quan đến nhân viên cho các hệ thống con khác, đảm bảo mọi hệ thống có thể hoạt động hiệu quả dựa trên thông tin cập nhật và đồng nhất.  



# 3. Mô Tả Các Phụ Thuộc Của Hệ Thống Con

### Mối Quan Hệ Giữa Các Hệ Thống Con

Mối quan hệ giữa các hệ thống con trong kiến trúc được thiết kế rõ ràng và có tổ chức nhằm đảm bảo tính dễ hiểu và khả năng mở rộng trong tương lai. Chi tiết về các phụ thuộc giữa các hệ thống con như sau:

- **Timecard Subsystem**  
  Hệ thống này chịu trách nhiệm ghi nhận và lưu trữ thông tin giờ làm việc của nhân viên. Để thực hiện chức năng của mình, **Timecard Subsystem** cần truy xuất dữ liệu từ **Employee Management Subsystem**, nơi lưu trữ thông tin chi tiết về nhân viên. Sự phụ thuộc này đảm bảo rằng mọi dữ liệu liên quan đến nhân viên được đồng bộ và chính xác.

- **Payroll Processing Subsystem**  
  Đây là hệ thống phụ trách xử lý bảng lương cho nhân viên. Để hoàn thành quy trình tính lương, hệ thống này cần thu thập dữ liệu từ hai nguồn:  
  - **Employee Management Subsystem**: Dữ liệu từ hệ thống này cung cấp danh sách nhân viên cùng các thông tin cần thiết như mức lương cơ bản, hợp đồng, và các yếu tố liên quan.  
  - **Timecard Subsystem**: Thông tin về giờ làm việc từ hệ thống này được sử dụng để tính toán chính xác lương theo số giờ làm việc hoặc theo các chính sách đã định.

- **Scheduler Subsystem**  
  Hệ thống này được thiết kế độc lập, không có bất kỳ phụ thuộc trực tiếp nào vào các hệ thống con khác. Tuy nhiên, **Scheduler Subsystem** đóng vai trò quan trọng trong việc tự động kích hoạt **Payroll Processing Subsystem** theo lịch trình đã được định trước. Điều này giúp đảm bảo rằng bảng lương được xử lý kịp thời và chính xác mà không cần sự can thiệp thủ công.

Các mối quan hệ trên được thiết kế nhằm tối ưu hóa luồng dữ liệu giữa các hệ thống, đồng thời giữ cho kiến trúc tổng thể dễ bảo trì và nâng cấp.

# 4. Kiểm Tra (Checkpoints)

- **Phân chia hợp lý**: Các hệ thống con trong toàn bộ kiến trúc được thiết kế với trách nhiệm rõ ràng và cụ thể. Mỗi hệ thống con đảm nhận một vai trò nhất định, giúp tăng cường khả năng quản lý và giảm sự chồng chéo trong quá trình vận hành. Các thành phần trong từng hệ thống con cũng được phân bổ hợp lý để đảm bảo tính nhất quán và hiệu quả.
- 
- **Phụ thuộc rõ ràng**: Mối quan hệ giữa các hệ thống con được mô tả một cách minh bạch thông qua sơ đồ kiến trúc và định nghĩa rõ các phụ thuộc. Điều này giúp việc theo dõi và bảo trì dễ dàng hơn, đồng thời tránh những vấn đề phát sinh do phụ thuộc không rõ ràng hoặc không được kiểm soát.
- 
- **Tính mở rộng**: Hệ thống được thiết kế với khả năng mở rộng linh hoạt, cho phép các hệ thống con thay đổi hoặc nâng cấp độc lập mà không ảnh hưởng đến hoạt động chung. Điều này đảm bảo rằng hệ thống luôn có khả năng thích nghi với các yêu cầu mới, đồng thời tối ưu hóa tài nguyên và thời gian phát triển.


  # Thiết Kế Hệ Thống Con Cho Ca Sử Dụng TimeCard

# 1. Phân Phối Hành Vi Của Hệ Thống Con Đến Các Phần Tử

### Thành Phần Hệ Thống Con
- **TimecardForm**: Giao diện người dùng để nhập và hiển thị thông tin thời gian làm việc.  
- **TimecardController**: Điều khiển logic và xử lý các yêu cầu từ TimecardForm.  
- **ProjectManagementDatabase**: Cơ sở dữ liệu để lưu trữ thông tin thời gian làm việc.  
- **Timecard**: Đối tượng đại diện cho các thông tin thời gian làm việc, bao gồm ngày và số giờ làm.  

---

# 2. Tài Liệu Hóa Các Phần Tử Của Hệ Thống Con

### Các Thành Phần Và Phương Thức

#### TimecardForm
- **displayTimecard()**: Hiển thị thông tin thời gian làm việc hiện tại.  
- **saveTimecard()**: Lưu thông tin giờ làm việc từ nhân viên.  

#### TimecardController
- **getChargeCodes()**: Lấy mã chi phí để nhập số giờ.  
- **getCurrentTimecard()**: Trả về thông tin thời gian làm việc hiện tại.  
- **updateTimecard()**: Cập nhật thông tin giờ làm việc.  

#### ProjectManagementDatabase
- **saveTimecard()**: Lưu thông tin thời gian vào cơ sở dữ liệu.  

#### Timecard
- Chứa các thuộc tính:  
  - **date**: Ngày làm việc.  
  - **hours**: Số giờ làm việc.  

---

# 3. Mô Tả Các Phụ Thuộc Của Hệ Thống Con

### Mối Quan Hệ Giữa Các Thành Phần
- **Nhân viên (Employee)**: Là tác nhân tương tác với hệ thống, sử dụng TimecardForm để nhập thông tin về thời gian làm việc.  
- **TimecardForm**: Gọi đến **TimecardController** để thực hiện logic và lưu dữ liệu.  
- **TimecardController**: Tương tác với **ProjectManagementDatabase** để lưu trữ thông tin thời gian làm việc.  

---

# 4. Kiểm Tra (Checkpoints)

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


