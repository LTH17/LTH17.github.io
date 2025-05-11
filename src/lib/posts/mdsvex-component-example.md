---
title: "Hệ thống phân tán"
date: "2023-04-28"
updated: "2023-04-28"
categories:
  - "sveltekit"
  - "markdown"
  - "svelte"
coverImage: "/images/jerry-zhang-ePpaQC2c1xA-unsplash.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Hệ thống phân tán.
---

<script>
	import Callout from '$lib/components/Callout.svelte';
</script>

# LTH17Group1.github.io
# 📅 28/04/2025

# 📖 Blog: Hệ thống phân tán - Lương Trung Hiếu

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Distributed_systems.svg/800px-Distributed_systems.svg.png" alt="Distributed System Illustration" width="600"/>

## 1. Hệ thống phân tán là gì?

Hệ thống phân tán (Distributed System) là tập hợp các máy tính độc lập, phối hợp với nhau để đạt được một mục tiêu chung. Các máy tính này giao tiếp với nhau thông qua mạng và hoạt động như một hệ thống duy nhất đối với người dùng cuối.

## 2. Các ứng dụng của hệ thống phân tán

- **Mạng xã hội và truyền thông**: Facebook, Twitter.
- **Thương mại điện tử**: Amazon, Shopee.
- **Ngân hàng và tài chính**: Hệ thống giao dịch trực tuyến 24/7.
- **Trò chơi trực tuyến**: PUBG, Liên Quân Mobile.

## 3. Các khái niệm chính của hệ thống phân tán

### 🔹 Scalability (Khả năng mở rộng)
Hệ thống có thể mở rộng để xử lý khối lượng công việc lớn hơn bằng cách thêm tài nguyên.

### 🔹 Fault Tolerance (Khả năng chịu lỗi)
Hệ thống vẫn tiếp tục hoạt động ngay cả khi một số thành phần gặp sự cố.

### 🔹 Availability (Tính sẵn sàng)
Đảm bảo hệ thống luôn sẵn sàng phục vụ người dùng.

### 🔹 Transparency (Tính trong suốt)
Người dùng không cần biết về cấu trúc hay địa chỉ thực tế của dịch vụ.

### 🔹 Concurrency (Tính đồng thời)
Nhiều tác vụ được xử lý cùng lúc mà không xung đột.

### 🔹 Parallelism (Tính song song)
Các tác vụ được phân chia và xử lý đồng thời trên nhiều bộ xử lý.

### 🔹 Openness (Tính mở)
Hệ thống được xây dựng dựa trên các chuẩn mở, dễ dàng tích hợp thêm thành phần.

### 🔹 Vertical Scaling (Mở rộng chiều dọc)
Nâng cấp phần cứng cho một máy chủ đơn lẻ (RAM, CPU).

### 🔹 Horizontal Scaling (Mở rộng chiều ngang)
Thêm nhiều máy chủ mới để chia sẻ tải và tăng khả năng xử lý.

### 🔹 Load Balancer (Cân bằng tải)
Phân phối đều lưu lượng đến các máy chủ để tránh quá tải.

### 🔹 Replication (Sao chép dữ liệu)
Tạo ra các bản sao dữ liệu nhằm tăng độ tin cậy và khả năng phục hồi.

## 4. Ví dụ: Hệ thống thương mại điện tử

**Ví dụ Amazon**:

- **Scalability**: Thêm máy chủ vào hệ thống khi lượng truy cập tăng.
- **Fault Tolerance**: Một node gặp lỗi, node khác tiếp quản ngay lập tức.
- **Availability**: Website luôn online, không downtime.
- **Transparency**: Người dùng không thấy được máy chủ thực sự nào đang xử lý yêu cầu.
- **Concurrency & Parallelism**: Xử lý hàng triệu đơn hàng và tìm kiếm sản phẩm cùng lúc.
- **Openness**: Kết nối với các dịch vụ vận chuyển, thanh toán bên ngoài.
- **Vertical & Horizontal Scaling**: Tăng cấu hình server hoặc mở rộng thêm server.
- **Load Balancer**: Điều phối yêu cầu tới các server nhàn rỗi nhất.
- **Replication**: Dữ liệu khách hàng và đơn hàng được nhân bản nhiều nơi.

## 5. Kiến trúc của hệ thống phân tán

### 🌟 Kiến trúc Client-Server
- Máy khách (client) gửi yêu cầu, máy chủ (server) phản hồi.
- Ví dụ: Trình duyệt web - Server web.

### 🌟 Kiến trúc Peer-to-Peer (P2P)
- Các node vừa làm client vừa làm server.
- Ví dụ: Mạng chia sẻ tệp BitTorrent.

### 🌟 Kiến trúc Microservices
- Ứng dụng chia nhỏ thành các dịch vụ độc lập.
- Ví dụ: Netflix.

### 🌟 Kiến trúc Service-Oriented Architecture (SOA)
- Các dịch vụ giao tiếp qua chuẩn như SOAP, WSDL.

### 🌟 Kiến trúc Event-Driven
- Các thành phần giao tiếp qua các sự kiện bất đồng bộ.
- Phù hợp với hệ thống thời gian thực như Uber.

## 6. Ví dụ thực tế: Hệ thống Hadoop

**Hadoop** là một nền tảng xử lý dữ liệu lớn theo kiến trúc phân tán:

- **Scalability**: Dễ dàng mở rộng cluster bằng cách thêm node.
- **Fault Tolerance**: Nếu một node thất bại, dữ liệu đã có bản sao trên các node khác.
- **Parallelism**: Phân chia công việc thành nhiều phần để xử lý đồng thời.
- **Transparency**: Người dùng chỉ tương tác với một lớp trừu tượng.

---

> **Viết bởi**: Lương Trung Hiếu  
> **Ngày**: 28/04/2025  
> **Nguồn tham khảo**: Slide bài giảng Hệ thống phân tán, Google, Wikipedia.

