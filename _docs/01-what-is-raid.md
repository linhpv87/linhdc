---
title: "What is Raid"
permalink: /docs/what-is-raid/
toc: true
tags:
  - Raid
---

## **RAID LÀ GÌ ?**

 RAID là chữ viết tắt của Redundant Array of Independent Disks. RAID là công nghệ ảo hóa lưu trữ dữ liệu kết hợp nhiều thành phần ổ đĩa vật lý thành một ổ đĩa logic duy nhất nhằm mục đích dự phòng dữ liệu, cải thiện hiệu suất hoặc cả hai.

 Mục tiêu chính của RAID là nâng cao tính khả dụng và an toàn của dữ liệu. RAID ngăn ngừa tình trạng không hoạt động xảy ra khi một ổ đĩa cứng hư hỏng, tuy nhiên nó không thể phục hồi được dữ liệu đã được người dùng xóa hoặc bị phá hủy khi gặp sự cố lớn như trộm cắp dữ liệu hay hỏa hoạn. Vì vậy, thường xuyên Sao lưu dự phòng cho dữ liệu của bạn là việc bắt buộc phải làm để giữ cho hệ thống của bạn được an toàn khỏi các sự cố này sau khi đã lắp đặt một hệ thống RAID.

Mỗi cấp độ RAID lại phục vụ một mục tiêu khác nhau dựa trên những nhu cầu cụ thể để giải quyết các yêu cầu nhất định như:

- Độ tin cậy của dữ liệu/ Data Reliability  - đảm bảo dữ liệu không có lỗi.
- Tính sẵn sàng của dữ liệu/ Data Availability – đảm bảo dữ liệu khả dụng ngay cả trong trường hợp lỗi phần cứng.
- Hiệu suất dữ liệu/ Data Performance – đảm bảo truy cập dữ liệu nhanh chóng cho cả hoạt động đọc và ghi.
- Dung lượng dữ liệu/ Data Capacity – đảm bảo khả năng lưu trữ lượng dữ liệu lớn.

## **Các kỹ thuật lưu trữ Raid**

Có 3 phương pháp lưu trữ dữ liệu chính trong mảng là:

**Striping:** Tách luồng dữ liệu thành các khối có kích thước nhất định (được gọi là “block size”), sau đó ghi từng khối này thông qua raid. Cách lưu trữ dữ liệu này làm tăng hiệu suất đọc/ghi dữ liệu.

**Mirroring:** là một kỹ thuật lưu trữ trong đó các bản sao dữ liệu giống hệt nhau được lưu trữ đồng thời trên các thành viên RAID. Kiểu sắp xếp dữ liệu này ảnh hưởng đến khả năng chịu lỗi cũng như hiệu suất.

**Parity:** là một kiểm tra dự phòng đảm bảo bảo vệ hoàn toàn dữ liệu mà không cần duy trì một bộ dữ liệu trùng lặp đầy đủ. Nó là  kỹ thuật lưu trữ sử dụng phương pháp striping và checksum. Checksum (dịch nôm na là kiểm tra tổng) thường được sử dụng để xác minh tính toàn vẹn dữ liệu. Trong kỹ thuật này, một hàm parity nhất định được tính cho khối dữ liệu. Nếu một ổ đĩa bị lỗi, khối bị thiếu sẽ được tính toán lại từ checksum, cung cấp khả năng chịu lỗi RAID.

Tất cả các các loại raid hiện có đều dựa trên striping, mirroring, parity hoặc kết hợp các kỹ thuật lưu trữ này.

## **CÁC CẤP ĐỘ RAID THƯỜNG SỬ DỤNG**

### **1. RAID 0 (striping):**

Cấp RAID này kết hợp từ hai ổ đĩa cứng trở lên theo cách các dữ liệu từ người dùng được cắt ra thành nhiều khối có thể quản lý được. Các khối này được phân tán lên khắp các ổ đĩa khác nhau trong mảng đĩa RAID 0. Bằng cách thực hiện này, kết hợp hai hay nhiều ổ cứng, hiệu năng đọc/ghi, đặc biệt là khả năng truy cập tuần tự, có thể được cải thiện. Tuy nhiên, không có dữ liệu dự phòng nào (parity) được lưu trên mảng RAID 0 cả, nghĩa là nếu một đĩa cứng hư hỏng, tất cả dữ liệu sẽ bị mất. Thiếu dữ liệu dự phòng cũng được thể hiện bởi con số 0, chỉ ra rằng chẳng có dữ liệu dự phòng nào cả. RAID 0 vì vậy luôn không được dùng trong những máy chủ có quan tâm nhiều đến vấn đề an toàn.

**Ưu điểm:** Tốc độ đọc ghi dữ liệu nhanh nhất, nếu càng nhiều ổ đĩa kết hợp tốc độ đọc ghi càng cao.

**Nhược điểm:** Không dự phòng dữ liệu, tức là nếu có một đĩa bất kỳ trong mảng bị hư hỏng  thì tất cả mọi dữ liệu sẽ bị mất.

**Số lượng ổ cứng:** Tối thiểu cần sử dụng 2 ổ cứng (Raid 0 có thể tạo từ 1 ổ cứng).

**Dung lượng:** Dung lượng của ổ đĩa logic sẽ bằng tổng dung lượng của các đĩa tham gia vào mảng. Ví dụ sử dụng 4 ổ dung lượng 240G để tạo Raid 0, tổng dung lượng của ổ đĩa logic thu được sẽ là 4 x 240 = 840G

**Ứng dụng:** Raid 0 sử dụng tốt nhất cho việc lưu trữ những dữ liệu không quan trọng nhưng yêu cầu đọc và ghi tốc độ cao. Trong thực tế raid 0 thường được sử dụng làm cache cho live streaming video  và chỉnh sửa video.

### **2. RAID 1 (mirroring):**

Raid 1 hay disk mirroring là quá trình sao chép dữ liệu vào nhiều hơn 1 ổ đĩa. Cả 2 đĩa hoạt động cùng lúc trong cùng 1 thời gian, do đó có thể đọc dữ liệu từ trên cả 2 ổ đĩa và điều này làm tăng tốc độ đọc. Tuy nhiên thao tác ghi dữ liệu sẽ chậm vì mỗi thao tác ghi sẽ thực hiện 2 lần.

Với Raid 1 dữ liệu sẽ được ghi trên cả 2 ổ cứng , do đó dữ liệu của bạn sẽ khả dụng ngay cả khi 1 ổ đĩa bị hỏng và máy chủ của bạn vẫn hoạt động bình thường. Ổ đĩa bị lỗi chỉ có thể thay thế bằng cách thủ công.

**Lưu ý:** Không nên nhầm lẫn giữa Raid 1 với bản sao dữ liệu của bạn. Raid 1 giải quyết cụ thể các vấn đề do phần cứng gây ra và bản thân raid 1 không thể khôi phục các file mà do bạn xóa nhầm hoặc bị hỏng do sự cố của ứng dụng hoặc sự cố khác.

**Uu điểm:**
- Khả năng hoạt động liên tục cao, một đĩa có thể hư, nhưng Ổ Đĩa Logic vẫn có dữ liệu để sử dụng.
- Thời gian xây dựng lại Raid (Rebuild) nhanh chóng.

**Nhược điểm:** Cần phải có 2 đĩa nhưng chỉ sử dụng được có một đĩa để lưu trữ ứng dụng.

**Số lượng ổ cứng:** Raid 1 yêu cầu tối thiểu 2 ổ cứng.

**Dung lượng:** Dung lượng của mảng Raid 1 sẽ bằng dung lượng của 1 ổ thành viên. Ví dụ sử dụng 2 ổ 240G tạo mảng Raid 1 thì ổ đĩa logic sẽ có dung lượng bằng 240G.

**Ứng dụng:** Thường được dùng cho các máy chủ chạy các ứng dụng trong giao dịch như bảng lương, tài chính, kế toán; các máy chủ chạy dịch vụ email; các máy chủ chạy website vừa và nhỏ không yêu cầu quá cao về tốc độ đọc, ghi; và dùng để chạy hệ điều hành.

### **3. RAID 5:**

Raid 5 sử dụng cả kỹ thuật striping và parity. Cung cấp cải thiện tốc độ đọc xấp xỉ như raid 0. 

RAID 5 sử dụng block level trong đó dữ liệu và các parity được phân tán lên tất cả mọi ổ đĩa. Mảng đĩa RAID 5 cho năng suất cân đối hơn. Ngay cả với những khối dữ liệu nhỏ, rất thường gặp trong những môi trường đa nhiệm và đa người dùng, thời gian đáp ứng rất tốt.

RAID 5 cho độ an toàn cao: Khi một ổ đĩa hư hỏng, tất cả mọi dữ liệu cũng vẫn có đầy đủ để sử dụng. Dữ liệu bị mất được tìm lại bằng cách dùng các parity để xác định phần dữ liệu còn lưu lại.

**Ưu điểm:** Khả năng hoạt động liên tục cao, một đĩa có thể hư, nhưng Ổ Đĩa Logic vẫn có dữ liệu để sử dụng, tận dụng được dung lượng đĩa để lưu trữ (mảng n đĩa, n-1 đĩa được dùng để lưu trữ).

**Nhược điểm:** 
- Phải tính toán thông tin dữ liệu dự phòng, gây hạn chế hiệu năng ghi đĩa.
- Thời gian xây dựng lại Raid (rebuild) chậm.

**Số lượng ổ cứng:** Raid 5 yêu cầu ít nhất 3 ổ đĩa.

**Dung lượng:** Dung lượng mảng raid 5 sẽ bằng (Dung lượng 1 ổ cứng) x [(Số lượng ổ cứng tham gia) – 1]. Ví dụ sử dụng 4 ổ cứn dung lượng 240G tạo mảng Raid 5 thì dung lượng của ổ đĩa logic = 240 x (4 -1) = 720G

**Ứng dụng:** Cấu hình RAID 5 mang lại hiệu quả lưu trữ cao và nó có thể được sử dụng để xây dựng các ứng dụng lưu trữ chung chẳng hạn như hệ thống lưu trữ tệp, tin tức và máy chủ ứng dụng cũng như máy chủ email không chứa thông tin nhạy cảm; Các máy chủ xử lý giao dịch trực tuyến (OLTP), máy chủ web, các ứng dụng yêu cầu hoạt động đọc và ghi ở mức độ cao, chẳng hạn như video streaming, web content, video-on-demand. Nếu tổ chức của bạn yêu cầu hoạt động đọc và ghi hiệu suất cao nhưng có ngân sách eo hẹp, cấu hình RAID 5 có thể là lựa chọn lý tưởng.

### **4. RAID 6:**

Raid 6 là phần mở rộng của raid 5 và sử dụng khối parity bổ sung.

Tương tự như RAID 5, Raid 6  sử dụng block level striping với 2 khối parity được phân phối trên tất cả các đĩa thành viên. RAID 6 tạo tới 2 parity cho 1 dữ liệu vì thế RAID 6 tăng khả năng chịu lỗi ( có thể hư tới 2 ổ đĩa ).

RAID 6 cung cấp khả năng chịu lỗi ở mức cao nhất và mang lại hiệu suất đọc tuyệt vời tương tự như RAID 0, tuy nhiên, hiệu suất ghi có thể bị giảm (và chậm hơn một chút so với RAID 5) do phải tính toán cập nhật hai khối parity cho mỗi thao tác ghi. Ngoài ra, hiệu suất đọc cũng có thể bị ảnh hưởng raid ở chế độ degraded mode, tức là trong trường hợp ổ đĩa bị lỗi.

**Ưu điểm:** Dự phòng dữ liệu, hiệu suất đọc cao.
**Nhược điểm:** 
- Giảm hiệu suất ghi do phải tính toán cập nhật 2 khối parity cho mỗi thao tác ghi. 
- Chi phí cao do phải sử dụng 2 đĩa để dành cho parity.
- Thời gian xây dựng lại Raid (rebuild) chậm.

**Số lượng ổ cứng:** Raid 6 yêu cầu tối thiểu 4 ổ đĩa.
Dung lượng: Dung lượng của một mảng RAID 6 với N ổ đĩa sẽ bằng kích thước của ổ đĩa nhỏ nhất x (N-2).  Ví dụ sử dụng 5 đĩa 240G chạy Raid 6, dung lượng ổ đĩa logic sẽ là: 240G x (5 -2) = 720G.

**Ứng dụng:** Raid 6 là sự lựa chọn tốt nhất cho các ứng dụng quan trọng và nhạy cảm.

### **5. RAID 10:**

RAID 10 là sự kết hợp của RAID 0 và RAID 1 trong đó dữ liệu được phân chia theo nhiều nhóm ổ đĩa RAID 1, như thể hiện trong hình dưới đây. RAID 10 còn được gọi là span mirroring.

RAID 10 cung cấp khả năng chịu lỗi bằng cách duy trì lỗi một ổ đĩa trong mỗi span và nó mang lại hiệu suất rất tốt với quá trình xử lý I/O đồng thời trên tất cả các ổ đĩa.

**Ưu điểm:** Hiệu suất đọc ghi cao và bảo vệ dữ liệu (cho phép lỗi 1 ổ trên mỗi span) với thời gian xây dựng lại Raid (rebuild) nhanh chóng.

**Nhược điểm:** 
- Chi phí đắt đỏ, chỉ một nửa số đĩa được dùng cho lưu trữ.
- Số lượng ổ đĩa hạn chế (tối đa 16 ổ đĩa).

**Số lượng ổ cứng:** RAID 10 yêu cầu ít nhất 4 ổ đĩa.
Dung lượng:  Dung lượng của một mảng RAID 10 bằng một nửa tổng dung lượng lưu trữ. Ví dụ sử dụng 4 ổ 240G tạo Raid 10, dung lượng sẽ bằng (4 x 240):2 = 480G.

**Ứng dụng:** Lý tưởng cho các máy chủ cơ sở dữ liệu và bất kỳ môi trường nào có nhiều dữ liệu nhỏ ngẫu nhiên được ghi.

### **6. Raid 50:**

RAID 50 là sự kết hợp của RAID 0 và RAID 5, trong đó dữ liệu được phân chia theo nhiều nhóm ổ đĩa RAID 5, như thể hiện trong hình dưới đây. RAID 50 còn được gọi là spanned striping với phân phối parity.

RAID 50 cung cấp khả năng chịu lỗi bằng cách duy trì lỗi một ổ đĩa trong mỗi span (Span ở đây được hiểu là tầng thấp hơn của mảng, được kết hợp để tạo nên tầng tiếp theo khi thảo luận về các cấp độ raid lồng nhau; như hình trên thì ta có 1 raid 0 từ  2 span raid 5) và nó mang lại hiệu suất đọc tuyệt vời. Nó cũng cải thiện hiệu suất ghi so với RAID 5 do tính toán parity riêng biệt trong mỗi span. 

**Ưu điểm:** 
- Cung cấp hiệu suất đọc tuyệt vời. 
- Tăng khả năng bảo vệ mà không phải tốn nhiều chi phí như mảng Raid 10.
- Tăng thông lượng dữ liệu và dự phòng.
Nhược điểm : 
- Yêu cầu nhiều ổ đĩa.
- Đắt hơn so với raid 5.
- Thời gian xây dựng lại Raid (Rebuild) chậm.

**Số lượng ổ cứng :** Raid 50 yêu cầu tối thiểu 6 ổ đĩa.
Dung lượng : Dung lượng Raid 50 = dung lượng của S * (N-1) disk, với S là số span và N là số lượng ổ đĩa trên mỗi span. Ví dụ Raid 50 với 6 ổ đĩa 240G, tức là sẽ có 2 span raid 5 (mỗi span 3 ổ đĩa) kết hợp thành 1 raid0, dung lượng = 2 * (3 - 1) * 240G = 960G

**Ứng dụng:** Raid 50 sử dụng tốt nhất cho các ứng dụng cần độ tin cậy cao và xử lý các yêu cầu tốc độ cao và truyền dữ liệu cao với chi phí ổ đĩa thấp hơn so với mảng raid 10. Chẳng hạn như sử dụng làm storage cho streaming video.

### **7. Raid 60:**

RAID 60 là sự kết hợp của RAID 0 và RAID 6 trong đó dữ liệu được phân chia theo nhiều nhóm ổ đĩa RAID 6, như thể hiện trong hình dưới đây. RAID 60 còn được gọi là span striping với parity được phân tán trên 2 ổ đĩa.

RAID 60 cung cấp khả năng chịu lỗi tốt nhất bằng cách duy trì hai lỗi ổ đĩa đồng thời trong mỗi span và nó mang lại hiệu suất đọc tuyệt vời. Nó cũng cải thiện hiệu suất ghi so với RAID 6 do tính toán parity riêng biệt trong mỗi span.

**Ưu điểm:**
- Hiệu suất cao hơn so với Raid 6, đặc biệt trong quá trình ghi. 
- Có thể duy trì 2 ổ đĩa lỗi trên mỗi mảng Raid 6 nên rất an toàn.
Nhược điểm : 
- Yêu cầu nhiều ổ đĩa.
- Đắt hơn so với Raid 50 1 chút do cần thêm ổ đĩa cho tính toán parity.
- Thời gian xây dựng lại Raid (Rebuild) chậm.

**Số lượng ổ cứng:** Raid 60 yêu cầu tối thiểu 8 ổ đĩa.

**Dung lượng:** Dung lượng Raid 60 = dung lượng của S * (N-2) disk, với S là số span và N là số lượng ổ đĩa trên mỗi span. Ví dụ Raid 60 với 8 ổ đĩa 240G, tức là sẽ có 2 span raid 6 (mỗi span 4 ổ đĩa) kết hợp thành 1 raid0, dung lượng = 2 * (4 - 2) * 240G = 960G

**Ứng dụng:** Raid 60 tương tự như raid 50 nhưng cung cấp nhiều dự phòng hơn, nên nó đặc biệt hữu ích cho các giải pháp lưu trữ dữ liệu lớn và tính sẵn sàng cao, các máy chủ không được backup (như máy chủ lưu trữ video xử lý số lượng lớn Camera).

### **8. Hot Spares:**

Hot Spares (Ổ đĩa dự phòng nóng) là ổ đĩa được chỉ định thay thế ổ đĩa bị lỗi một cách tự động và minh bạch trong mảng RAID có khả năng chịu lỗi. Điều này giúp giảm thiểu lượng thời gian khi mảng vẫn ở chế độ degraded  sau khi ổ đĩa bị lỗi bằng cách tự động bắt đầu quá trình xây dựng lại để khôi phục dữ liệu từ ổ đĩa bị lỗi trên ổ dự phòng nóng. Ổ đĩa dự phòng nóng có thể là Global hoặc Dedicated. Ổ đĩa Global hot spare có thể được sử dụng để thay thế ổ đĩa bị lỗi trong bất kỳ nhóm ổ đĩa chịu lỗi nào miễn là dung lượng của nó bằng hoặc lớn hơn dung lượng của ổ đĩa bị lỗi được sử dụng bởi mảng RAID. Ổ đĩa  dedicated hot spare chỉ có thể thay thế ổ đĩa bị lỗi trong nhóm ổ đĩa được chỉ định.

## **Triển khai Raid:**

Raid có thể tạo bằng 2 cách khác nhau:

**Software raid:** sử dụng trình điểu khiển hệ điều hành.

**Hardware raid:** sử dụng phần cứng đặc biệt.

### **1. Software Raid:**

Software Raid là 1 trong những giải pháp Raid rẻ nhất.
Trong Software RAID, việc triển khai RAID là một ứng dụng chạy trên máy chủ. Loại RAID này sử dụng các ổ đĩa được gắn vào hệ thống máy tính thông qua giao diện I/O tích hợp hoặc bộ điều hợp bus máy chủ không cần bộ xử lý (HBA). RAID sẽ hoạt động ngay sau khi HĐH đã tải phần mềm trình điều khiển RAID.

Phương pháp này không yêu cầu bất kỳ thiết bị bổ sung nào để kết nối các thiết bị lưu trữ. Tuy nhiên, nó có thể làm tăng tải xử lý tổng thể trên máy chủ và có thể làm chậm quá trình tính toán RAID cũng như các quy trình khác đang được thực hiện trên thiết bị.

RAID phần mềm chạy hoàn toàn trên CPU của hệ thống máy chủ.

**Ưu điểm:** Chi phí thấp hơn do không cần phần cứng dành riêng cho RAID. 

**Nhược điểm:**  Hiệu suất RAID thấp hơn vì CPU cũng cung cấp năng lượng cho HĐH và ứng dụng.

### **2. Hardware Raid:**

RAID phần cứng được tạo bằng phần cứng riêng biệt. Về cơ bản có hai lựa chọn:
- Sử dụng RAID-on-Chip (ROC) tích hợp trên các bo mạch chủ.
- Tùy chọn đắt tiền hơn là sử dụng PCIe controller card. Những bộ điều khiển như vậy có thể được trang bị CPU riêng, bộ nhớ cache dự phòng bằng pin và chúng thường hỗ trợ trao đổi nóng. 

Bộ điều khiển xử lý tất cả các chức năng RAID trong bộ xử lý và bộ nhớ phần cứng của chính nó. CPU máy chủ không phải tải khối lượng công việc lưu trữ nên nó có thể tập trung xử lý các yêu cầu phần mềm của hệ điều hành máy chủ và các ứng dụng.

**Ưu điểm:** 
- Hiệu suất tốt hơn Software RAID. 
- Không sử dụng CPU của máy chủ.
- Cho phép người dùng tạo phân vùng khởi động.
- Card điều khiển có thể dễ dàng hoán đổi để thay thế và nâng cấp.

**Nhược điểm:** 
- Đắt hơn Software RAID.
- Khi bộ điều khiển RAID gặp sự cố, nó nên được thay thế bằng bộ điều khiển tương tự để tránh sự cố. Nếu không có bộ điều khiển mới ngay lập tức, chức năng hệ thống có thể bị chậm trễ.

## **Lựa chọn cấp độ Raid phù hợp:**

Các yếu tố cần xem xét khi chọn cấp độ RAID phù hợp bao gồm: 

- Dung lượng
- Hiệu suất
- Dự phòng (độ tin cậy/an toàn)
- Giá cả

Bảng sau đây tóm tắt các cấp độ RAID và đặc điểm của chúng để hỗ trợ bạn chọn cấp độ RAID thích hợp nhất cho nhu cầu của mình hay tư vấn cho khách hàng.

Ghi chú:
* Số lượng ổ đĩa tối đa trong một mảng RAID phụ thuộc vào bộ điều khiển và hệ thống.
** Lên đến 8 span với 2 ổ đĩa trên mỗi span.
- Các thuật ngữ Excellent, Very good, Good, và Satisfactory là các chỉ số hiệu suất tương đối nhằm mục đích so sánh và không đại diện cho bất kỳ giá trị tuyệt đối nào. Mức độ: Excellent > Very good > Good > Satisfactory.
- Các thuật ngữ Fast và Slow là các chỉ báo thời gian xây dựng lại tương đối nhằm mục đích so sánh và không đại diện cho bất kỳ giá trị tuyệt đối nào: Fast > Slow.
- Degraded array performance có nghĩa là hiệu suất của mảng RAID với một hoặc nhiều ổ đĩa bị lỗi.
Bảng sau đây tóm tắt các lợi ích và hạn chế của từng cấp độ RAID.

Một điều quan trọng cần lưu ý là RAID không thể thay thế cho Backup!

Tất cả các cấp độ RAID ngoại trừ RAID 0 đều cung cấp khả năng bảo vệ khỏi lỗi một ổ đĩa. Một hệ thống RAID 6 thậm chí còn tồn tại khi 2 đĩa chết đồng thời. Để bảo mật hoàn toàn, bạn vẫn cần sao lưu dữ liệu được lưu trữ trên hệ thống RAID. 

Bản sao lưu đó sẽ có ích nếu tất cả các ổ đĩa bị lỗi đồng thời do nguồn điện tăng đột biến. 

Đó là một biện pháp bảo vệ khi hệ thống lưu trữ bị đánh cắp. Sao lưu có thể được giữ bên ngoài ở một vị trí khác. Điều này có thể hữu ích nếu thiên tai hoặc hỏa hoạn phá hủy nơi làm việc của bạn. 

Lý do quan trọng nhất để sao lưu nhiều thế hệ dữ liệu là lỗi người dùng. Nếu ai đó vô tình xóa một số dữ liệu quan trọng và điều này không được chú ý trong vài giờ, vài ngày hoặc vài tuần, một bộ sao lưu tốt sẽ đảm bảo bạn vẫn có thể truy xuất các tệp đó.

