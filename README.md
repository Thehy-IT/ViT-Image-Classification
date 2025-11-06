# Dự án: Phân loại ảnh sử dụng Vision Transformer (ViT)

## 1. Giới thiệu
Dự án này nhằm mục tiêu xây dựng và huấn luyện mô hình **Vision Transformer (ViT)** để thực hiện **phân loại ảnh** trên tập dữ liệu **Tiny ImageNet** hoặc **CIFAR-100**.  
Bên cạnh đó, nhóm tiến hành **so sánh hiệu suất giữa ViT và mô hình CNN** có cùng số lượng tham số, đồng thời **trực quan hóa cơ chế Attention** của mô hình Transformer.

---

## 2. Mục tiêu
- Áp dụng kiến trúc **Vision Transformer** vào bài toán phân loại ảnh.  
- So sánh hiệu năng giữa **ViT và CNN** khi có cùng quy mô tham số.  
- Trực quan hóa và phân tích cơ chế **Attention** trong mô hình ViT.

---

## 3. Tập dữ liệu
Dự án sử dụng một trong hai tập dữ liệu sau:

- **Tiny ImageNet**: gồm 200 lớp, mỗi lớp có 500 ảnh huấn luyện, kích thước ảnh 64×64.  
- **CIFAR-100**: gồm 100 lớp, mỗi lớp có 600 ảnh, kích thước ảnh 32×32.


## 4. Kiến trúc mô hình

### Vision Transformer (ViT)
Mô hình ViT bao gồm các thành phần chính:
- **Patch Embedding**: Chia ảnh đầu vào thành các ô nhỏ (patch) và mã hóa chúng thành vector.  
- **Transformer Encoder**: Gồm các lớp Self-Attention và Feed Forward kết hợp với cơ chế chuẩn hóa và residual connection.  
- **Classification Head**: Lớp tuyến tính (Linear) để dự đoán nhãn của ảnh.

### Mô hình CNN (đối chứng)
Xây dựng mô hình CNN có **số lượng tham số tương đương với ViT** nhằm đánh giá hiệu năng tương đối giữa hai mô hình.

---

## 5. Cấu hình huấn luyện
| Tham số | Giá trị |
|----------|----------|
| Số epoch | 50 |
| Kích thước batch | 64 |
| Bộ tối ưu | Adam |
| Learning rate | 1e-4 |
| Hàm mất mát | CrossEntropyLoss |
| Bộ điều chỉnh tốc độ học | StepLR hoặc CosineAnnealingLR |
| Augmentation | RandomCrop, RandomHorizontalFlip, Normalize |

---

## 6. Môi trường và công cụ
- **Ngôn ngữ lập trình**: Python 3.10+  
- **Framework**: PyTorch  
- **Môi trường thực thi**: Jupyter Notebook  
- **Cài đặt thư viện cần thiết**:
  ```bash
  pip install torch torchvision numpy matplotlib tqdm scikit-learn

## 7. Đánh giá mô hình

Các chỉ số được sử dụng để đánh giá hiệu năng mô hình bao gồm:

- **Độ chính xác (Accuracy)**
- **Độ chính xác theo lớp (Precision, Recall, F1-score)**
- **Ma trận nhầm lẫn (Confusion Matrix)**
- **Đồ thị huấn luyện**: Loss và Accuracy trên tập train/validation
- **Trực quan hóa Attention Map** trong ViT

## 8. So sánh mô hình
| Mô hình      | Tập dữ liệu | Độ chính xác | Số tham số | Ghi chú                                |
| ------------ | ----------- | ------------ | ---------- | -------------------------------------- |
| ViT-Small    | CIFAR-100   | 78.3%        | 22M        | Huấn luyện chậm hơn, dễ giải thích hơn |
| CNN-ResNet18 | CIFAR-100   | 75.9%        | 21M        | Huấn luyện nhanh hơn, ít tham số hơn   |

## 9. Trực quan hóa Attention

Nhóm tiến hành trực quan hóa các bản đồ Attention của ViT để quan sát vùng ảnh mà mô hình tập trung trong quá trình nhận dạng:

## 10. Mở rộng nghiên cứu
- So sánh chi tiết ViT và CNN về thời gian huấn luyện, độ chính xác và tốc độ hội tụ.
- Phân tích biểu đồ Attention để hiểu rõ cơ chế học của mô hình.
- Tối ưu kiến trúc ViT cho các tập dữ liệu nhỏ.

## 11. Kết quả và nhận xét

ViT cho thấy khả năng học biểu diễn mạnh mẽ và khả năng tổng quát tốt trên tập dữ liệu nhỏ khi được huấn luyện đầy đủ.
So với CNN, ViT yêu cầu nhiều tài nguyên huấn luyện hơn nhưng cung cấp khả năng giải thích mô hình tốt hơn nhờ cơ chế Attention.