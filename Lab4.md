## Họ tên: Nguyễn Văn Trường
## Mã sinh viên: 4451051021
# PAYROLL SYSTEM USE CASE DESIGN SOLUTION

## 1. Login
### Các phần tử thiết kế gồm:
- Interface (LoginPage): có thể coi là interface vì nó đảm nhận vai trò giao tiếp trực tiếp với người dùng, thu thập thông tin đăng nhập (username, password) và hiển thị phản hồi dựa trên kết quả xử lý từ hệ thống.
- Subsystem (AuthService): là subsystem vì nó đóng vai trò xử lý toàn bộ logic nghiệp vụ liên quan đến xác thực, thực hiện kiểm tra thông tin đăng nhập và đảm bảo tính hợp lệ. AuthService không trực tiếp tương tác với người dùng mà chỉ xử lý dữ liệu và trả kết quả.
- DataBase: Đây là nơi lưu trữ dữ liệu người dùng - sử dụng MySQL
### Biều đồ Sequence:
![Biểu đồ Sequence Login](https://www.planttext.com/api/plantuml/png/Z9B1IiD048Rl-nHBJmtO5-X1AbP1y21KlQY7wUwOBcnsmymaqcVo4NeG-aA-WhiDJTDInHn2PdQ--Vw5V6--PYn0qbHUWP58-ecHL9rQphWQWkZHzjC5GNe7WzlDQxYFfGiFKE980-k-EcMuMVAQ1QlCN3MoMY2rpdJKeFwJcuF04hY3zeLIEQEUN1xaKnrhF2GR5-T6qkRAoQunRj9nW0elT0tC7v5ieVhHp0qIJdKBtbaGl2Qq6CI1vxCR1b3UiGyyrILA3fGRFLYe_RcUd0e9fQ7G8uLIu4M_E7xEITwKJi-HxFYcFdyk6cEGkw35ZXXSCCtdxTba7Q6HnpW7NYqZa4qwz2bLqjs5zl_2Mt0UC_sRopgkFQnlY29bIR1gbbxvt_i1003__mC0)

### Lý do thiết kế:
#### 1. Đảm bảo tính bảo mật
- AuthService chịu trách nhiệm xử lý xác thực, giúp cách ly việc xử lý logic với giao diện người dùng (LoginPage). Điều này giảm thiểu nguy cơ rò rỉ thông tin nhạy cảm hoặc tấn công trực tiếp từ giao diện.
- Thông tin đăng nhập được xác thực thông qua một cơ chế cụ thể (ví dụ: mã hóa mật khẩu, kiểm tra với cơ sở dữ liệu).
#### 2. Phù hợp với kiến trúc MVC (Model-View-Controller)
- Model: MySQL làm nơi lưu trữ dữ liệu người dùng.
- View: LoginPage hiển thị và tương tác với người dùng.
- Controller: AuthService làm nhiệm vụ xử lý logic xác thực.
#### **3. Dễ bảo trì và mở rộng**
##### **Mở rộng chức năng**
Hệ thống được thiết kế linh hoạt, cho phép dễ dàng bổ sung các tính năng mới, chẳng hạn:
- **Xác thực hai bước (2FA):**
  - AuthService có thể được mở rộng để thêm logic kiểm tra mã OTP (One-Time Password) nhằm tăng cường bảo mật.
- **Ghi nhật ký đăng nhập thất bại:**
  - Bổ sung logic trong AuthService để lưu thông tin các lần đăng nhập thất bại vào bảng **LoginLogs** trong cơ sở dữ liệu, phục vụ mục đích giám sát và phân tích.

##### **Thay đổi công nghệ**
Hệ thống được phân tách rõ ràng giữa các tầng, đặc biệt là tầng truy xuất dữ liệu, giúp việc thay đổi công nghệ trở nên dễ dàng:
- Nếu cần chuyển đổi từ MySQL sang PostgreSQL hoặc MongoDB, chỉ cần sửa đổi tầng truy xuất dữ liệu mà không ảnh hưởng đến các thành phần khác như LoginPage hoặc AuthService.
- Điều này đảm bảo hệ thống vừa linh hoạt vừa tương thích với nhiều công nghệ cơ sở dữ liệu hiện đại.


## 2. Maintain Employee Information
### Các phần tử thiết kế gồm:

- Interface (EmployeeUI): là interface vì nó đóng vai trò là giao diện người dùng, nơi người dùng thực hiện các thao tác nhập liệu và nhận kết quả từ hệ thống. Giao diện này cho phép người dùng cung cấp thông tin về nhân viên và hiển thị các thông tin kết quả sau khi thực hiện các thao tác như thêm, sửa, xóa nhân viên.
- Subsystem (EmployeeController): Là hệ thống con chịu trách nhiệm xử lý các yêu cầu từ giao diện người dùng. Nó nhận các thao tác từ EmployeeUI (như thêm, sửa hoặc xóa nhân viên) và thực thi các nghiệp vụ liên quan, chẳng hạn như kiểm tra tính hợp lệ của dữ liệu và gọi các phương thức của cơ sở dữ liệu để thao tác với thông tin nhân viên.
- DataBase: Đây là nơi lưu trữ dữ liệu nhân viên - sử dụng MySQL
### Biểu đồ Sequence:
![Biểu đồ Sequence Maintain Employee Information](https://www.planttext.com/api/plantuml/png/h9InQiCm48PtFSNXoO7c1JAKXAP3jaBnr7QuI9SYa2LLaWS_KnyXGo4lr5UeOiUnd2PWbtgmqLdVVxhFuE_zrz87TA4g5KCUZ8F2asCsbYIN5dM0xF0fTI2tGqw7_Qj-BAqoDL6noG0zzCjBobTRN_j0PKez61sSKOhSWExBJ630BNg2h7kvFbK6H5Tax7XYcDyd9rc0iNHk-OJlbC-kRdFqKP4FAnwaqJasZpkWfCMCCLG1NbP2dCat1l7gSzBKVf05e11TEHzcfdnFf3dTU6DJklqmlt4ORlHEkZBEaT_kVw57I6yLrf5vhZWdxoDAMfoK53P-AffifMgmVn0pEcYictQWoNfQx9gXDIdwWo7HOBy6suXfVaR6ZBNJ3ZFPJeiDxIpZxVZ7-G400F__0m00)
### Lý do thiết kế:

#### 1. **Tính tách biệt rõ ràng**
- Các thành phần như giao diện người dùng (UI), logic xử lý nghiệp vụ (Controller), và cơ sở dữ liệu (Database) được tách biệt rõ ràng, giúp hệ thống dễ dàng mở rộng và bảo trì.
- Việc tách rời giúp mỗi phần chỉ tập trung vào nhiệm vụ riêng của nó, không ảnh hưởng đến các phần khác trong hệ thống, đồng thời giảm thiểu sự phụ thuộc và làm cho mã nguồn trở nên dễ quản lý hơn.

#### 2. **Tính dễ bảo trì**
- Khi mỗi thành phần của hệ thống được tách biệt, việc bảo trì hoặc sửa chữa sẽ trở nên đơn giản và nhanh chóng hơn. 
- Nếu có sự thay đổi trong một phần của hệ thống (chẳng hạn như thay đổi giao diện người dùng hoặc thay đổi quy trình xử lý trong controller), các phần khác sẽ không bị ảnh hưởng và có thể tiếp tục hoạt động bình thường.
- Điều này giúp giảm thiểu thời gian downtime và rủi ro khi triển khai các bản cập nhật mới.

#### 3. **Tăng tính linh hoạt**
- Việc tách biệt các thành phần trong hệ thống giúp chúng ta dễ dàng thay đổi hoặc mở rộng hệ thống khi cần thiết mà không làm gián đoạn các phần còn lại của ứng dụng.
- Ví dụ, nếu yêu cầu thay đổi công nghệ cơ sở dữ liệu hoặc bổ sung thêm chức năng mới (như thêm tính năng báo cáo), chúng ta có thể thực hiện mà không ảnh hưởng đến các chức năng chính của hệ thống.
- Thiết kế này cũng tạo ra nền tảng vững chắc cho việc phát triển và mở rộng hệ thống trong tương lai.

## 3. Maintain Purchase Order
### Các phần tử thiết kế gồm:
- Interface (CommissionedEmployeeInterface): Đây là phần giao diện người dùng dành cho nhân viên có trách nhiệm tương tác trực tiếp với hệ thống, giúp họ thực hiện các thao tác liên quan đến thông tin đơn hàng.
- Subsystem (MaintainPurchaseOrderController): Là phần hệ thống xử lý các yêu cầu từ người dùng, thực hiện các nghiệp vụ như thêm mới, cập nhật hoặc xóa thông tin đơn hàng trong hệ thống.
- PurchaseOrderDataBase: Đây là nơi lưu trữ dữ liệu đơn hàng - sử dụng MySQL
### Biểu đồ Sequence:
![Biểu đồ Sequence Maintain Purchase Order ](https://www.planttext.com/api/plantuml/png/Z9CnJiCm58PtdyBgb4Zj1JgWGiEG0O4G0n8mkFOhYUJOaVqYr6Dm0peZ9hPsG6eHz-W9k0AEcn2Q1AcH8iVE-p___vFzlVwOM6G6YqmInb4REjLPbbgRQWNYFCkbNW2Gt9MaFCsPGZhOlAOAmSmPXytwNlK9uhfWG9cbdTKspnOpkx08MScxO0xltgl2y8HPk3G2p5GhD5fAC9xOJ8bWo6QkhEJKtoNcG1vLFxoudX3IPvsEJhg6nvGdMbiuvUYAWv1qAafPusfCSwCvM5i9c1-6L7ipuE996nB29DAxczrggUddyzTIqMJxeXuV27LF0olHjMTdn033VQhW45UgwZewQlanW8LHNXP7Us4SXPsT-iFRH3zrfA14bM2wMxtbL2LkmEE3p05vugbdYxQbOs9KkGFnD_z_cnMvEEnQ70shHV7Rm2RHxVQT7Pz4W8GMl8Br71CVg7lizas-1bj838mVGZ9naF9c_W000F__0m00).

### Lý do thiết kế

#### 1. **Tách biệt rõ ràng các thành phần**
- **Giao diện người dùng (CommissionedEmployeeInterface)**: Giao diện này đảm nhận việc giao tiếp trực tiếp với nhân viên. Nhân viên có thể thực hiện các thao tác như tạo mới, cập nhật hoặc xóa thông tin đơn hàng thông qua giao diện này. Việc tách giao diện ra giúp giảm sự phụ thuộc giữa người dùng và các logic nghiệp vụ.
  
- **Hệ thống con xử lý nghiệp vụ (MaintainPurchaseOrderController)**: Phần này đóng vai trò quan trọng trong việc xử lý các yêu cầu từ người dùng và thực thi các nghiệp vụ liên quan đến đơn hàng. MaintainPurchaseOrderController nhận thông tin từ giao diện người dùng, xử lý logic nghiệp vụ và giao tiếp với cơ sở dữ liệu để thực hiện các thao tác như thêm, sửa, xóa đơn hàng.
  
- **Cơ sở dữ liệu (PurchaseOrderDataBase)**: Đây là nơi lưu trữ thông tin đơn hàng. Cơ sở dữ liệu sử dụng MySQL để lưu trữ các thông tin chi tiết của đơn hàng, cho phép truy xuất và quản lý thông tin hiệu quả. Việc tách biệt cơ sở dữ liệu giúp dễ dàng quản lý và bảo trì dữ liệu trong hệ thống mà không làm ảnh hưởng đến các phần khác.

#### 2. **Dễ dàng mở rộng và thay đổi**
- **Mở rộng chức năng dễ dàng**: Với thiết kế tách biệt, khi có yêu cầu thêm các tính năng mới như quản lý thông tin đơn hàng phức tạp hơn, việc mở rộng hệ thống chỉ cần thay đổi hoặc bổ sung vào phần subsystem (MaintainPurchaseOrderController) mà không làm ảnh hưởng đến giao diện người dùng hay cơ sở dữ liệu.
  
- **Chuyển đổi công nghệ dễ dàng**: Khi cần nâng cấp hoặc thay đổi công nghệ (ví dụ chuyển từ MySQL sang PostgreSQL), ta chỉ cần thay đổi phần cơ sở dữ liệu mà không làm ảnh hưởng đến các phần giao diện và nghiệp vụ. Điều này giúp hệ thống linh hoạt và dễ dàng thích ứng với các thay đổi trong công nghệ.

#### 3. **Tăng tính bảo trì**
- **Cập nhật và sửa chữa dễ dàng**: Khi có lỗi hoặc cần nâng cấp một phần của hệ thống, vì các thành phần được tách biệt rõ ràng, việc sửa chữa chỉ cần can thiệp vào một phần cụ thể mà không ảnh hưởng đến các thành phần khác. Điều này giúp giảm thiểu rủi ro và chi phí bảo trì hệ thống.
  
- **Khả năng kiểm tra và debug dễ dàng**: Việc tách biệt các phần giao diện, nghiệp vụ và cơ sở dữ liệu giúp việc kiểm tra, debug và xử lý sự cố trở nên dễ dàng hơn, vì các phần này không bị phụ thuộc vào nhau và có thể kiểm tra độc lập.

## 4. Run Payroll
### Các phần tử thiết kế gồm:
- Interface (PayrollInterface): Đây là giao diện người dùng cho phép người sử dụng yêu cầu thông tin bảng lương và hiển thị kết quả tính toán bảng lương cho nhân viên.
- Interface (BankSystemInterface): Giao diện này cho phép hệ thống tương tác với ngân hàng, thực hiện các thao tác cần thiết như chuyển tiền và kiểm tra trạng thái tài khoản.
- Subsystem (RunPayrollController): Đây là phần hệ thống con xử lý quy trình tính toán bảng lương cho nhân viên, bao gồm việc thu thập dữ liệu từ các thành phần khác và thực hiện các tính toán cần thiết để tạo bảng lương.
- PurchaseOrderDataBase: Đây là nơi lưu trữ dữ liệu nhân viên và bảng lương, thực hiện các thao tác truy vấn và cập nhật - sử dụng MySQL
### Biểu đồ Sequence:
![Biểu đồ Sequence Run Payroll](https://www.planttext.com/api/plantuml/png/b5HBRi8m4Dtd55x2eXT02D525smGAk80WpEq5lxL7bFbR5tqIBr2xM28476Rhc9vtdipy_oKxy-lkITm59IiW9DnREVHLJPU2IuiQ68RQ9oHSgK9tG4uikbKNCwpsGtq2VHnstX2DGJz4dJMNXXDwOikmdtO-rOZmciWs8D7jio7gahpiOVP_LWJvl0zeATS6OshEqpazNQTiDQ5NDWumz7xAD0BZYANSIBn5UbPMMaQn7Gx6hFgMYstSqZ1wLjYiLj1WuFaGG9Xjt19eSUiMdWheScLRL0AN5FmhFKyUlHcFd9vYGH29ekk3rAO4gnrvZHWnWB_X4uSchks9PM-24wOq8B4sIc5cYA_3_UBrKOVX5EPlZgh2QF_lqvq-VZeSyAm7fQnOElkcRS45985WsEsQ-cBymv_pTqJ5MseUuA5YQ75B38iB1rbdPG4lymmHrsdFyyF0000__y30000)

### Lý do thiết kế

#### 1. **Tính mở rộng và bảo trì cao**:
   - **Subsystem (RunPayrollController)**: Việc giữ lại logic nghiệp vụ tính lương trong một subsystem riêng biệt giúp cho việc nâng cấp hoặc thay đổi quy trình tính lương trở nên dễ dàng mà không ảnh hưởng đến các thành phần khác trong hệ thống. Nếu có thay đổi về cách tính toán bảng lương hoặc yêu cầu mới, chỉ cần điều chỉnh subsystem mà không cần thay đổi giao diện hay cơ sở dữ liệu.
   
   - **PurchaseOrderDataBase (MySQL)**: Việc sử dụng cơ sở dữ liệu MySQL giúp lưu trữ thông tin về nhân viên và bảng lương một cách hiệu quả, dễ dàng quản lý và truy xuất dữ liệu. Hệ thống có thể dễ dàng mở rộng và kết nối với các hệ thống khác nếu cần thiết mà không gặp phải vấn đề tích hợp.

#### 2. **Tính linh hoạt**:
   - **Interface (BankSystemInterface)**: Giao diện này tạo ra sự linh hoạt trong việc tương tác với hệ thống ngân hàng, cho phép dễ dàng thay đổi hoặc cập nhật các giao dịch mà không cần phải thay đổi các thành phần khác của hệ thống.

## 5. Select Payment
### Các phần tử thiết kế gồm:
- Interface (PaymentInterface): Đây là giao diện mà người dùng tương tác trực tiếp với hệ thống để lựa chọn phương thức thanh toán phù hợp với nhu cầu của mình.
- Subsystem (PaymentController): Là thành phần chịu trách nhiệm xử lý logic nghiệp vụ liên quan đến việc lựa chọn và thực hiện phương thức thanh toán của người dùng, bao gồm việc định tuyến và kiểm tra các thao tác thanh toán.
- Subsystem (PickUpSystem): Quản lý và thực hiện quy trình thanh toán theo phương thức "Pick-up", nơi người dùng có thể lên lịch để thanh toán trực tiếp.
- Subsystem (MailSystem): Xử lý các thanh toán thông qua việc gửi thông báo và thực hiện thanh toán qua thư điện tử, giúp người dùng thực hiện giao dịch trực tuyến nhanh chóng.
- Subsystem (BankSystem): Quản lý và thực hiện thanh toán qua chuyển khoản ngân hàng, đặc biệt là các giao dịch thông qua hình thức chuyển khoản trực tiếp (Direct Deposit).
- DataBase: Là nơi lưu trữ dữ liệu về phương thức thanh toán mà người dùng đã chọn, giúp hệ thống theo dõi và cập nhật thông tin mỗi khi người dùng thay đổi hoặc thực hiện giao dịch thanh toán - sử dụng MySQL.
### Biểu đồ Sequence:
![Biểu đồ Sequence Select Payment](https://www.planttext.com/api/plantuml/png/d9H1RiCW44NtFWNAgbta0b5aHQqtNKI9LEK014za50m8ngfojYvwf5wXO1CPdDYDiqFmt_3d3_Rlzy_68ZNOr2AZ39KX1micqswBCwwfHBAdbneaVaW4Sw8Co7hDh-iyloTzLnAD4WACqzhcQ2yMeHvgEJiVz6TxD27RKYx-5RrHURuhAYdI8xL0Yh38CjyVMUQtRQs81G4Cmy4Mi5Bbosjs8-pXg557L-ehxEyqSYLj3qT2HxSM0j2cu9iiG2lB8tJAAQkKij31Sons3Gwmr5mo5uUm2if6H7V5voFtC2LFtDH16YgKOpTUP-F0Hhk9GJg1XI-pRFJYaKXyahC3IQ7KNFJ-LeHBZjmPz9j1xRX8Cfr7A-oOfuBm_4Cf5DoujiABcXt729rwZJwvFfSX6Occaqd0lL4Ch7t-mNJLI2Zd4zk0BFqlxWy00F__0m00)

### Lý do thiết kế

#### 1. **Quản lý các phương thức thanh toán linh hoạt**:
   - **Subsystem (PickUpSystem)**: Đảm bảo rằng các thanh toán qua phương thức "Pick-up" được lên lịch và thực hiện một cách tự động, giúp người dùng dễ dàng chọn thời gian thanh toán mà không phải thao tác thủ công.
   
   - **Subsystem (MailSystem)**: Hỗ trợ thanh toán qua thư điện tử giúp nâng cao tính tiện dụng cho người dùng khi giao dịch trực tuyến, đảm bảo hệ thống có thể xử lý các phương thức thanh toán khác nhau.

   - **Subsystem (BankSystem)**: Xử lý thanh toán qua chuyển khoản ngân hàng (Direct Deposit) một cách an toàn và hiệu quả, đáp ứng yêu cầu thanh toán cho các giao dịch tài chính lớn hoặc xuyên biên giới.

#### 2. **Dễ dàng bảo trì và mở rộng**:
   - **Database (MySQL)**: Việc lưu trữ thông tin phương thức thanh toán trong cơ sở dữ liệu MySQL giúp việc truy xuất và quản lý dữ liệu trở nên đơn giản và hiệu quả. Khi cần thay đổi hoặc bổ sung các phương thức thanh toán mới, chỉ cần cập nhật cơ sở dữ liệu mà không làm gián đoạn hệ thống.
   
   - **Tính mở rộng**: Thiết kế này cho phép dễ dàng mở rộng để thêm vào các phương thức thanh toán mới mà không làm ảnh hưởng đến các thành phần hiện tại của hệ thống. Các subsystem riêng biệt giúp dễ dàng thay đổi hoặc nâng cấp từng phần của hệ thống mà không cần ảnh hưởng đến toàn bộ hệ thống.

## 6. Maintain Timecard
### Các phần tử thiết kế gồm:
- Interface (TimecardInterface): Đây là giao diện mà người dùng sử dụng để nhập và theo dõi thời gian làm việc của mình. Giao diện này cung cấp các chức năng để người dùng dễ dàng tương tác và cập nhật thời gian làm việc.
- Subsystem (TimecardController): Là bộ điều khiển chịu trách nhiệm tiếp nhận và xử lý các yêu cầu của người dùng liên quan đến việc nhập, sửa đổi và theo dõi thời gian làm việc. Subsystem này đảm bảo rằng tất cả các thao tác được thực hiện chính xác và hiệu quả.
- DataBase: Dây là nơi lưu trữ dữ liệu về thời gian làm việc của nhân viên. - sử dụng MySQL.
### Biểu đồ Sequence:
![Biểu đồ Sequence Maintain Timecard](https://www.planttext.com/api/plantuml/png/d9H1ReD034Ntd6AMxQ8NYA8e4ksYKdTf3k20IKOQPgXjKd6sBdgaNg4pK1AW2O7iHjZ_V_inyFFrlMO1aZ8t4IJYI6qPAIhy8vte0goeTvrZ0fI-Ma7A846rNEhsl5fTx8sT5NB68FbcBdTSiM3kcrCGs06ZUluxH548L4-h2paBPTnUsuV7w7-j8-Y4BTGHZFOX65nZmXIjQ33SyUYqUvDsZY15qbdL5vtAr_88fIHx5cq4fBmUTsd9L7DXe7eBkvxaerW8FqfaQKkp06KeoQ6jXFMceDcZz2HXkCbm9eMDW1deHycKHNZveVBYtQjPP0RQgMmOZhYjfUbWqfjy4cSpJNbRQrnc8UA3-no4tqBaFyTSttTt-j8vW3QriZ_bN3or1xDszfvRT5R7ZIr8unIjqQRX__SB003__mC0)

### Lý do thiết kế

#### 1. **Dễ dàng bảo trì và nâng cấp**:
   - Thiết kế tách biệt giữa giao diện và xử lý nghiệp vụ giúp dễ dàng nâng cấp từng phần mà không làm ảnh hưởng đến các thành phần khác trong hệ thống. Nếu cần thay đổi logic xử lý thời gian làm việc, ta chỉ cần can thiệp vào `TimecardController`, còn giao diện `TimecardInterface` không cần thay đổi.
   
   - Các thành phần riêng biệt cũng giúp việc bảo trì hệ thống trở nên đơn giản hơn, bởi mỗi phần có thể được kiểm tra và sửa chữa độc lập mà không gây gián đoạn cho các chức năng khác của hệ thống.

#### 2. **Tăng tính linh hoạt**:
   - Việc tách biệt giao diện và xử lý nghiệp vụ giúp hệ thống linh hoạt hơn trong việc mở rộng hoặc thay đổi tính năng. Nếu trong tương lai có thêm yêu cầu mới liên quan đến thời gian làm việc, chỉ cần điều chỉnh subsystem mà không phải làm lại toàn bộ hệ thống.

## 7. Create Employee Report
### Các phần tử thiết kế:
- Interface (EmployeeUI): Đây là giao diện người dùng, nơi nhân viên có thể nhập các dữ liệu đầu vào như tiêu chí báo cáo hoặc mã số công việc. Đồng thời, giao diện này cũng hiển thị kết quả đầu ra, bao gồm các báo cáo được tạo ra từ hệ thống.
- Subsystem (EmployeeReportController): Đây là bộ điều khiển xử lý các yêu cầu tạo báo cáo. Nó đóng vai trò kết nối và điều phối giữa các hệ thống con như ReportGenerator và ReportStorage. Subsystem này xử lý các logic nghiệp vụ, bao gồm việc xác định dữ liệu cần thiết để tạo báo cáo và lưu trữ kết quả cuối cùng.
- Entity (ReportGenerator, Report, ReportStorage): Các thành phần này có chức năng tạo báo cáo và lưu trữ báo cáo. Report là kết quả dữ liệu, và ReportStorage lưu trữ báo cáo trong MySQL.
### Biểu đồ Sequence:
![Biểu đồ Sequence Create Employee Report](https://www.planttext.com/api/plantuml/png/Z9DBRi8m48RtFeN5YaZq0WWXn4EeYqfLGWym90DrSUpKdhJAsRheaNg5ZlCYBVJ1maAPxn_F_q_oyVQ-y0IEobmBICawkSaBRIj4KV1ZbQe23FKF7subUCddRAOCeJj0YlFvLJJ6mZfQMKFEQeqk23VnYfM-tFlA4-RVb8rYYmOTX4bO46-PHqEAggjmpVoE9DmAZbYJoH3DW60F7kMziq-OqXqOvdAkhvU1vdCswo3cHUTCtimvWgciWsikYV6vH4_ZI70sN6QZN4UJjIaunM4f6AVjdqY0xZrGLQ0SxIo1be-sT5w-MdV2J1uuXA8PRYGa_q9-t7szdCeZqWxyQMKpz7njgFB0DztTrDM6kZ1qfdoXeJfhUx9fSc4IDL_VuJqT2JOdshxnDinJhwrTUszq8iyANcQ0fp9r-0TvDk9gIbmwQELDFH9re0cyOAS8PeRBuD8NoKGUb4O3EKwajYcGiYOQfXKdOSNM_LV6RrS_TMhDGRayp3EEVbX1AAuQhkuoRZ9Ty16-nay0003__mC0)

### Lý do thiết kế

#### 1. **Dễ bảo trì và nâng cấp**:
   - Thiết kế tách biệt giữa giao diện và nghiệp vụ giúp dễ dàng bảo trì, nâng cấp hoặc thay đổi các thành phần mà không gây ảnh hưởng đến các phần khác của hệ thống. Ví dụ, nếu cần thay đổi cách thức tạo báo cáo, ta chỉ cần chỉnh sửa **EmployeeReportController**, trong khi giao diện người dùng **EmployeeUI** vẫn không thay đổi.

#### 2. **Tính mở rộng và linh hoạt**:
   - Việc phân chia rõ ràng giữa giao diện người dùng và xử lý nghiệp vụ giúp hệ thống linh hoạt hơn trong việc mở rộng và thay đổi. Nếu trong tương lai cần thêm các loại báo cáo hoặc tính năng mới, hệ thống có thể dễ dàng mở rộng mà không ảnh hưởng đến các phần còn lại của ứng dụng.

## 8. Create Administrative Report
#### Ở ca sử dụng này, ta phân tách thành hai biểu đồ Sequence: Tạo báo cáo và lưu báo cáo.
#### Các phần tử thiết kế: 
- Interface: PayrollAdministratorUI (UI) - Đây là giao diện người dùng mà người quản lý bảng lương sẽ tương tác trực tiếp với hệ thống. Giao diện này giúp người sử dụng dễ dàng cung cấp dữ liệu đầu vào và nhận kết quả báo cáo từ hệ thống.
- Hệ thống con (Subsystem):
  + ReportController (RC): Đây là hệ thống con trung gian chịu trách nhiệm xử lý các logic nghiệp vụ, điều phối các thao tác giữa các thành phần như UI, ReportGenerator, và ReportStorage. Nó giúp đảm bảo rằng các yêu cầu từ giao diện người dùng được thực thi chính xác và dữ liệu báo cáo được xử lý đúng cách.
  + ReportGenerator (RG): Đây là hệ thống con chuyên biệt đảm nhiệm việc tạo báo cáo. Nó nhận các yêu cầu từ ReportController và thực hiện các thao tác tính toán, xử lý dữ liệu để tạo ra các báo cáo phù hợp theo yêu cầu.
  + Report (R): Đây không phải interface hoặc hệ thống con, mà là một đối tượng dữ liệu (data object), được tạo ra trong quá trình xử lý và lưu trữ trong MySQL.
#### Biểu đồ Sequence Tạo báo cáo
![Biểu đồ Sequence Create Report](https://www.planttext.com/api/plantuml/png/b991QiGW58RtESLRjZ1pWI1XGWgXcpO4vW1lp6kn9CRgoyAppQ97wXNwD9dIGXQj2n7z_j__5p-l7wV0w7cPnW8rpnuwZ7uUntgOZ3M1FQPD3D3LXHFGQEFGyYvsVaoWpA2KiKp-1JLLrIzTJsxstCoMavooTT_0RIWLbak8WMdQ5RPawJjItyAVXPc7lQ4KMJOSHLPqDHmhQL22f_U50ZUUa6crkDFUI2c3zuLq5AvlIj3xW5HAG5l2wvhuXd1qT83yvW-oUm2omxQOt3X7eYUSI0pQRF3p0f4yNzv8_yEa0NNCAJpnuksQOJFfSurqBZK64zo8SGifHoUnJ9_Y2m00__y30000)
### Biểu đồ Sequence Lưu báo cáo
![Biểu đồ Sequence Save Report](https://www.planttext.com/api/plantuml/png/Z9E_QXj14CRxUuefBR1VG1p2GW7XnXO7xjoiLYDfpDtkUM_ES7MA56xiEWGIN8G40YbSwJ0kpkGzzWdo2fvTot-4LMYBOPdxPkQRttB_suV3YfNZkiWJfTawcAZ6sJmVpWeoLB5J8Qagc0oJKeIagLI6jyfEZu9G8gGf6KOtLne7Wusw34lhU6GDXtAChRCHl9mqhUffrLICnTR2CHfyjPIDOUV2g8Tj9qtHC74ZPSba20S3sQ0F3Yzgh7ZaK34-jzZJZcGfKht4M4Pmj5WosBcWwSFnujzVttuZkAZzwjP0tjr3q_skGVlLpnhOhtvOc7OIj8GpS-dRhnJk6fYYRjdzWJrkIjo7-2IVPF0-e9cjBqMPsmRnM1NOInAXB4wpKH_qTek9K0sASHyMpz1UD3lF4BwXm-Q8a-avwjsRR9AINe_NlhqXu83hrYpUcC3ZJSpfDQpBxhj0yUql1RpixaJAP29E8mdogmUEIwO7SKc7N3kpuJ7h1KpXks2QKLNcgbapoDRESfn7O-79nwIio7pxnO3qRp-7ERwzUcTHBosOZo-T7ChsuHTw0W00__y30000)

### Lý do thiết kế

#### 1. **Tăng tính mở rộng và bảo trì**:
- Thiết kế này cho phép hệ thống dễ dàng mở rộng trong tương lai. Nếu cần thêm chức năng mới hoặc thay đổi cách thức xử lý báo cáo, chỉ cần điều chỉnh trong **ReportController** hoặc **ReportGenerator**, mà không ảnh hưởng đến các thành phần khác của hệ thống.
  
#### 2. **Tăng tính linh hoạt và khả năng thay đổi**:
- Khi các yêu cầu mới hoặc thay đổi công nghệ (ví dụ, thay đổi cách thức tạo báo cáo hoặc thay đổi phương thức lưu trữ), hệ thống có thể thay đổi mà không gây gián đoạn cho các phần khác của ứng dụng nhờ vào việc sử dụng các hệ thống con độc lập và giao diện người dùng rõ ràng.

