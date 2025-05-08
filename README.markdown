# Hệ Thống Gợi Ý Nghề Nghiệp dựa trên mạng Neuron đa lớp

## Giới thiệu
Dự án này xây dựng một hệ thống gợi ý nghề nghiệp sử dụng mô hình học máy **Multi-Layer Perceptron (MLP)** để dự đoán các nghề nghiệp phù hợp với học sinh dựa trên điểm số của các loại trí thông minh và các đặc điểm khác. 

Hệ thống nhằm hỗ trợ học sinh định hướng nghề nghiệp bằng cách phân tích các điểm mạnh của họ dựa trên lý thuyết **Đa trí thông minh** của Howard Gardner, bao gồm các loại trí thông minh như Linguistic, Musical, Bodily, Logical-Mathematical, Spatial-Visualization, Interpersonal, Intrapersonal, và Naturalist.

## Mô tả Dataset
Dataset được sử dụng trong dự án chứa thông tin về học sinh và các đặc điểm liên quan đến trí thông minh và nghề nghiệp. Cấu trúc của dataset bao gồm các cột sau:

- **Sr.No.**: Số thứ tự (có thể chứa giá trị NaN, không sử dụng trong mô hình).
- **Course**: Khóa học của học sinh (chưa được sử dụng trong mô hình, chứa giá trị NaN).
- **Job profession**: Nghề nghiệp mục tiêu (nhãn cần dự đoán, ví dụ: "Công an, Cảnh sát, Quân đội", "Phát thanh viên", "Dược sĩ",...).
- **Student**: Mã định danh học sinh (ví dụ: S3474, S3419,...).
- **Linguistic, Musical, Bodily, Logical-Mathematical, Spatial-Visualization, Interpersonal, Intrapersonal, Naturalist**: Điểm số (số nguyên) đại diện cho mức độ của từng loại trí thông minh, được sử dụng làm đặc trưng đầu vào cho mô hình.
- **s/p**: Mã học sinh trùng với cột Student (có thể dùng để kiểm tra tính nhất quán).
- **P1, P2, ..., P8**: Các cột bổ sung (có giá trị như POOR, AVG, BEST), có thể đại diện cho đánh giá hiệu suất hoặc đặc điểm khác, nhưng không rõ ràng trong việc sử dụng cho mô hình.

### Đặc điểm dataset
- **Số lượng mẫu**: 3415.
- **Nhãn (Job profession)**: Bao gồm nhiều loại nghề nghiệp khác nhau, từ các ngành kỹ thuật (Nhà toán học, Nhà địa chất học) đến nghệ thuật (Giáo viên âm nhạc, Biên tập viên âm thanh) và dịch vụ (Y tá, điều dưỡng, Thư ký công ty).
- **Đặc trưng**: Các cột điểm số trí thông minh là các giá trị số nguyên, có thể nằm trong một khoảng cố định (ví dụ: 0-20). Các cột P1-P8 có giá trị phân loại (POOR, AVG, BEST), nhưng không rõ vai trò trong mô hình.

## Các thành phần chính của mã nguồn
1. **Tiền xử lý dữ liệu**:
   - Các bước tiền xử lý bao gồm loại bỏ hoặc xử lý giá trị NaN, mã hóa nhãn nghề nghiệp (`Job profession`) và chuẩn hóa các đặc trưng đầu vào (điểm số trí thông minh).

2. **Huấn luyện mô hình**:
   - Mô hình **MLP** được sử dụng để dự đoán nghề nghiệp dựa trên các đặc trưng đầu vào.
   - Dữ liệu được chia thành tập huấn luyện và tập kiểm tra (tỷ lệ 8/2 trên mỗi ngành nghề).
   - Mô hình được lưu vào file `model.pkl` trong thư mục `/content/drive/MyDrive/Semes_4/AI/job_recommendation_final3/` để tái sử dụng.

3. **Dự đoán trên dữ liệu giả**:
   - Một tập hợp dữ liệu giả (`synthetic_data`) được tạo để kiểm tra khả năng dự đoán của mô hình. Mỗi mẫu dữ liệu chứa 16 giá trị đại diện cho điểm số của các loại trí thông minh và các đặc trưng khác.

## Yêu cầu cài đặt
Để chạy file `job_predict.ipynb`, bạn cần cài đặt các thư viện Python sau:
```bash
pip install pandas scikit-learn seaborn matplotlib numpy
```

Nếu sử dụng Google Colab, cần đảm bảo kết nối với Google Drive để truy cập dataset:
```python
from google.colab import drive
drive.mount('/content/drive')
```

### Yêu cầu phần cứng
- **Môi trường**: Jupyter Notebook hoặc Google Colab (khuyến nghị sử dụng Colab nếu cần GPU để huấn luyện mô hình nhanh hơn).
- **GPU**: Không bắt buộc, nhưng Colab cung cấp tùy chọn GPU (như T4) để tăng tốc độ huấn luyện.


## Liên hệ
Nếu bạn có thắc mắc hoặc cần hỗ trợ, vui lòng liên hệ qua email: [nductrien.ai@gmail.com].