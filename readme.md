# BÀI THỰC HÀNH HADOOP ONLINE - HỆ THỐNG DỮ LIỆU LỚN

**Đề tài:** Phân tích đơn hàng thương mại điện tử bằng HDFS và MapReduce

## 1. THÔNG TIN SINH VIÊN

* **Họ và tên:** Bùi Thị Thanh Hiền
* **Mã sinh viên (MSSV):** A47092
* **Môn học:** Dữ liệu lớn (IS330) - Hệ sinh thái Hadoop
* **Môi trường thực hành:** Google Colab (Hadoop Streaming & HDFS Pseudo-Distributed)

## 2. MỤC TIÊU BÀI THỰC HÀNH

* Thao tác thành thạo với hệ thống tệp phân tán **HDFS** (tạo thư mục, upload tập dữ liệu nguồn, kiểm tra phân vùng).
* Xây dựng và thực thi chương trình **MapReduce** bằng ngôn ngữ Python thông qua **Hadoop Streaming**.
* Lọc các giao dịch thương mại điện tử có trạng thái thành công (`status == SUCCESS`).
* Tổng hợp và tính toán tổng doanh thu theo từng nhóm sản phẩm (`category`).
* Xác định **Top 3 nhóm sản phẩm** có doanh thu cao nhất nhằm hỗ trợ ban quản trị tối ưu hóa tồn kho, chiến lược marketing và vận hành logistics.

## 3. DANH MỤC SẢN PHẨM NỘP BÀI

Theo quy ước đặt tên và yêu cầu cấu trúc nộp bài, thư mục/gói nộp bao gồm **03 tệp chính**:

1. **`orders_2026_09.csv`**
   * *Mô tả:* Bộ dữ liệu giao dịch đơn hàng thương mại điện tử thô mẫu tháng 09/2026 (chứa các trường thông tin: `transaction_id`, `province`, `category`, `amount`, `status`,...).
2. **`Hadoop_Ecommerce_Lab.ipynb`**
   * *Mô tả:* Tệp mã nguồn mở Google Colab ghi nhận toàn bộ quá trình thực hiện từ cài đặt môi trường Java/Hadoop, cấu hình HDFS/YARN, lập trình hàm `Mapper`/`Reducer` bằng Python, cho đến chạy job Hadoop Streaming và in kết quả phân tích.
3. **`readme.md`**
   * *Mô tả:* Tệp tài liệu hướng dẫn, mô tả kỹ thuật và báo cáo tổng quan kết quả thực hành (tệp này).

## 4. QUY TRÌNH THỰC HIỆN TRÊN GOOGLE COLAB (`Hadoop_Ecommerce_Lab.ipynb`)

* **Bước 1 & 2:** Cài đặt gói OpenJDK 17 và tải Apache Hadoop 3.5.0; thiết lập các biến môi trường (`HADOOP_HOME`, `JAVA_HOME`).
* **Bước 3 & 4:** Cấu hình SSH cục bộ, định dạng NameNode và khởi động các dịch vụ HDFS / YARN ở chế độ Pseudo-Distributed.
* **Bước 5 & 6:** Tạo và đưa file `orders_2026_09.csv` lên hệ thống lưu trữ phân tán HDFS tại thư mục `/user/student/ecommerce/input/`.
* **Bước 7 & 8:** Xây dựng script `mapper_revenue.py`, `reducer_revenue.py` và thực thi câu lệnh **Hadoop Streaming** qua jar file của hệ thống.
* **Bước 9:** Đọc, trích xuất và sắp xếp kết quả doanh thu qua thư mục output trên HDFS.

## 5. KẾT QUẢ PHÂN TÍCH & NHẬN XÉT KINH DOANH

| Hạng | Nhóm sản phẩm (Category) | Tổng doanh thu (VND) | Nhận xét & Đề xuất quản trị |
| :---: | :--- | :---: | :--- |
| **1** | **Electronics** | *Doanh thu cao nhất* | Chiếm tỷ trọng áp đảo trong tổng doanh thu. Doanh nghiệp cần ưu tiên phân bổ không gian kho bãi, chính sách bảo hiểm hàng hóa và dịch vụ vận chuyển nhanh. |
| **2** | **Home** | *Doanh thu đứng thứ hai* | Thể hiện nhu cầu tiêu dùng ổn định đối với các thiết bị gia dụng và đời sống. Cần duy trì các gói ưu đãi combo sản phẩm. |
| **3** | **Fashion** | *Doanh thu đứng thứ ba* | Mặt hàng có tính linh hoạt cao, phù hợp để đẩy mạnh các chiến dịch Flash-sale hoặc kích cầu theo mùa vụ. |

## 6. ĐÁNH GIÁ TỔNG QUAN

* **Về mặt kỹ thuật:** Nắm vững cấu trúc vận hành của hệ thống tệp phân tán HDFS và mô hình xử lý dữ liệu lớn theo lô (Batch Processing) sử dụng cơ chế Key-Value qua Hadoop Streaming.
* **Về mặt nghiệp vụ:** Các thông tin thống kê trực quan từ hệ thống phân tán giúp ban điều hành đưa ra các quyết định thực tế nhằm tối ưu nguồn lực kinh doanh.