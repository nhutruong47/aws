---
title: "Bản đề xuất"
date: 2025-09-09
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Đề xuất – Smart Resume Analyzer (Bộ Phân tích CV Thông minh)

_Giải pháp Serverless thống nhất trên AWS để phân tích CV so với JD và tạo Điểm Khớp (Fit Score)_

> **Lưu ý:** Đề xuất này tuân theo phong cách phân đoạn của mẫu `_index.md` trước đây nhưng đã được viết lại cho dự án Smart Resume Analyzer.

---

## 1) Tóm tắt Điều hành (Executive Summary)

**Smart Resume Analyzer** là một nền tảng web serverless đánh giá mức độ khớp giữa **CV** của ứng viên và **Mô tả Công việc (JD)**. Nó tính toán **Điểm Khớp (Fit Score)**, phát hiện **khoảng trống kỹ năng (skill gaps)** và cung cấp **đề xuất học tập cá nhân hóa**.
Giải pháp được triển khai bởi một nhóm 5 thành viên trong **4 tuần** trên **AWS** sử dụng các dịch vụ được quản lý, trả tiền theo mức sử dụng (pay-as-you-go) để giữ chi phí gần bằng 0 cho khối lượng công việc demo. Giao diện người dùng (UI) được xây dựng bằng **Next.js** và lưu trữ trên **AWS Amplify**; phần backend sử dụng **API Gateway + Lambda** với **DynamoDB**, **S3**, **Comprehend**, **Textract**, và **Cognito**.

**Kết quả chính**

- Sàng lọc CV nhanh hơn 90% cho các kịch bản demo.
- Điểm Khớp khách quan với các báo cáo trực quan.
- Lộ trình học tập khả thi cho từng ứng viên.

---

## 2) Xác định Vấn đề (Problem Statement)

### 2.1 Vấn đề là gì?

- Nhà tuyển dụng dành nhiều thời gian để đọc CV thủ công và so sánh chúng với JD.
- Ứng viên thiếu cái nhìn sâu sắc về những kỹ năng họ đang thiếu và cách cải thiện.
- Các công cụ hiện có đắt tiền hoặc không được điều chỉnh cho các trường hợp sử dụng tại Việt Nam/Đông Nam Á.

### 2.2 Giải pháp

- Tải lên CV (PDF/DOCX) và JD → trích xuất văn bản và xử lý ngôn ngữ tự nhiên (NLP) tự động.
- Phát hiện **kỹ năng, kinh nghiệm, giáo dục**; tính toán **Điểm Khớp (Fit Score)** so với JD.
- Đề xuất **lộ trình kỹ năng** được ánh xạ từ một kho **Bản thể học Kỹ năng (SkillOntology)** nhỏ.
- Đăng nhập bảo mật bằng **Cognito**; kết quả hiển thị trong một bảng điều khiển **Next.js** sạch sẽ.

---

## 3) Kiến trúc Giải pháp (Solution Architecture - tổng quan)

![Solution Architecture Diagram](https://i.ibb.co/ZR0VcspJ/Solution-Architecture.png)

Kiến trúc serverless, hướng sự kiện (event-driven) trên AWS.

**Các thành phần chính**

- **Frontend**: Giao diện người dùng Next.js (Amplify Hosting) để tải lên và hiển thị bảng kết quả.
- **Tầng API**: Amazon API Gateway → Các hàm AWS Lambda.
- **Xử lý (Processing)**:
    - `parseResume` → Textract (nếu là PDF được scan) → văn bản đã chuẩn hóa.
    - `nlpAnalyze` → Comprehend → thực thể/kỹ năng/cụm từ.
    - `recommendSkills` → so sánh với JD + `SkillOntology` trong DynamoDB.
- **Dữ liệu (Data)**: DynamoDB (kết quả, bản thể học), S3 (CV/JD tạm thời).
- **Danh tính (Identity)**: Cognito (mã truy cập JWT).
- **Vận hành (Ops)**: IaC với AWS SAM, CI/CD qua CodeBuild + CodePipeline, ghi nhật ký trong CloudWatch.

**(Sơ đồ kiến trúc Mermaid được cung cấp riêng.)**

---

## 4) Triển khai Kỹ thuật (Technical Implementation)

### 4.1 Ngăn xếp Công nghệ (Tech stack)

- **Backend**: .NET 8 (C# Minimal API trên Lambda)
- **Frontend**: Next.js + TailwindCSS (Amplify Hosting)
- **AWS**: Lambda, API Gateway, DynamoDB, S3, Cognito, Comprehend, Textract
- **IaC**: AWS SAM
- **CI/CD**: CodeBuild + CodePipeline

### 4.2 Luồng End-to-end

1. Người dùng xác thực qua **Cognito** và nhận JWT.
2. Frontend yêu cầu **URL đã ký trước (presigned URL)** đến **S3** → tải lên CV/JD.
3. API Gateway gọi **Lambda `parseResume`**:
      - Nếu là PDF scan → **Textract** → trích xuất văn bản; nếu không thì phân tích trực tiếp.
      - Dọn dẹp & chuẩn hóa → lưu các cấu phần tạm thời trên S3.
4. **Lambda `nlpAnalyze`** sử dụng **Comprehend** để phát hiện thực thể/kỹ năng → ghi kết quả vào **DynamoDB**.
5. **Lambda `recommendSkills`** tải **SkillOntology** từ DynamoDB → so sánh CV với JD → tính toán **Fit Score** + khoảng trống kỹ năng.
6. Frontend truy vấn kết quả qua API → hiển thị biểu đồ/bảng.

### 4.3 Mô hình Dữ liệu (DynamoDB – đơn giản hóa)

- **Bảng `Profiles`** (PK: `userId`, SK: `profileId`) – lưu trữ bản phân tích CV mới nhất.
- **Bảng `Analyses`** (PK: `analysisId`) – điểm khớp, khoảng trống kỹ năng, dấu thời gian.
- **Bảng `SkillOntology`** (PK: `skillId`, thuộc tính: `name`, `tags`, `learningPath[]`).

### 4.4 API (cấp độ cao)

- `POST /upload-url` → ký trước cho CV/JD.
- `POST /analyze` → kích hoạt pipeline cho một cặp khóa S3 đã cho.
- `GET /analyses/{id}` → trả về Fit Score & đề xuất.
- `GET /skills/{id}` → (tùy chọn) tìm kiếm lộ trình học tập của một kỹ năng.

---

## 5) Dòng thời gian & Các cột mốc (4 tuần)

| Tuần | Cột mốc                  | Sản phẩm bàn giao                                              |
| ---- | ------------------------ | -------------------------------------------------------------- |
| 1    | Nền tảng                 | SAM template, các bảng DynamoDB, Cognito, UI cơ sở             |
| 2    | Phân tích cú pháp & NLP  | `parseResume`, `nlpAnalyze`, phân tích JD, unit tests          |
| 3    | Bộ đề xuất & Tích hợp FE | `recommendSkills`, bảng điều khiển, biểu đồ                    |
| 4    | Demo & Tăng cường        | E2E tests, ghi nhật ký, điều chỉnh chi phí, slide thuyết trình |

---

## 6) Ước tính Ngân sách (quy mô demo)

_Mang tính chất tham khảo, giả định < 500 yêu cầu/tháng_

- **Lambda**: ~$0.02
- **API Gateway**: ~$0.01
- **S3** (vài GB, ít yêu cầu): ~$0.10
- **DynamoDB** (on-demand, R/W thấp): ~$0.05
- **Amplify Hosting**: ~$0.30
- **Comprehend + Textract (trang nhỏ)**: ~$0.40
- **Cognito**: $0.00
  **Tổng cộng ≈ $0.9 / tháng (~$10 / năm)**

---

## 7) Bảo mật, Rủi ro & Giảm thiểu

**Bảo mật**

- Các S3 bucket riêng tư với **SSE-KMS**; chỉ tải lên bằng URL đã ký trước.
- **IAM quyền hạn tối thiểu (least privilege)**; API được bảo vệ bằng **Cognito JWT**.
- **Che dấu PII (PII masking)** cho nhật ký; báo động **CloudWatch**.
- Tùy chọn: thiết lập quy tắc vòng đời để xóa CV/JD thô sau khi phân tích.

**Rủi ro & giảm thiểu**

- _Độ chính xác NLP_: Cung cấp các định dạng được hỗ trợ + dự phòng bằng quy tắc từ khóa.
- _CV lớn/không sạch_: Xác thực kích thước/định dạng; làm sạch trước khi NLP.
- _Đột biến chi phí_: Báo động AWS Budget; giới hạn số lượng trang cho mỗi yêu cầu.

---

## 8) Kết quả Mong đợi

- Khớp CV-JD tự động với **Điểm Khớp (Fit Score)** minh bạch.
- Phân tích trực quan về **các kỹ năng khớp so với khoảng trống kỹ năng** và **lộ trình học tập**.
- Ngăn xếp serverless, ít vận hành (low-ops) dễ dàng demo, mở rộng và bản địa hóa.

---

## 📄 Tài liệu Đề xuất (Google Docs)

👉 **Xem lại Đề xuất tại đây:**
[GOOGLE DOC LINK](https://docs.google.com/document/d/1ALFieRvZWl1Azg3C8a7L8Z-iL6-chpzS/edit?usp=sharing&ouid=100398969873071071371&rtpof=true&sd=true)
