---
title: "Deliverable 1 - Website"
date: "2025-05-11"
updated: "2025-05-11"
categories:
  - "sveltekit"
  - "markdown"
coverImage: "/images/jefferson-santos-fCEJGBzAkrU-unsplash.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Đề xuất đề tài mô tả vấn đề.
---

# Báo cáo CouchDB

## 1. Mục đích của thư viện CouchDB  
CouchDB là một cơ sở dữ liệu tài liệu (document database) mã nguồn mở, được thiết kế để có khả năng sẵn sàng cao, chịu phân vùng và đảm bảo tính nhất quán theo thời gian (eventually consistent). Thư viện này chủ yếu dùng để lưu trữ dữ liệu phi quan hệ dưới dạng JSON, đặc biệt phù hợp với các hệ thống phân tán.

## 2. Vấn đề mà thư viện giải quyết  
CouchDB giải quyết vấn đề lưu trữ và đồng bộ dữ liệu trong môi trường phân tán, đặc biệt là khi thiết lập nhiều bản sao (master-master) với khả năng tự động phát hiện và xử lý xung đột. Đây là một giải pháp phù hợp cho các hệ thống có yêu cầu cao về tính sẵn sàng và phân tán dữ liệu trên nhiều nút mạng.

## 3. Điểm mạnh của thư viện  
- **Khả năng đồng bộ mạnh mẽ**: Hỗ trợ đồng bộ hóa dữ liệu giữa nhiều thiết bị hoặc máy chủ một cách đáng tin cậy.  
- **Master-Master replication**: Cho phép nhiều máy chủ cùng ghi dữ liệu, phù hợp với mô hình phân tán.  
- **Chịu lỗi tốt**: Thiết kế để hoạt động ổn định trong môi trường có sự cố mạng hoặc chia tách mạng.  
- **Giao diện RESTful**: Tương tác dữ liệu thông qua HTTP API đơn giản, dễ tích hợp.  
- **Dữ liệu dạng JSON**: Linh hoạt và dễ quản lý trong các ứng dụng hiện đại.

## 4. Điểm yếu của thư viện  
- **Hiệu suất thấp hơn so với NoSQL chuyên biệt khác**: Trong một số trường hợp, tốc độ ghi và truy vấn không bằng MongoDB hoặc Redis.  
- **Quản lý xung đột dữ liệu phức tạp**: Khi dùng mô hình master-master, việc giải quyết xung đột đôi khi cần xử lý thủ công.  
- **Không phù hợp với dữ liệu quan hệ**: Không hỗ trợ JOIN hay ràng buộc khóa ngoại như các hệ quản trị cơ sở dữ liệu quan hệ.

## 5. So sánh với các thư viện/framework khác

| Tiêu chí                  | CouchDB                       | MongoDB                      | Firebase Realtime DB         |
|--------------------------|-------------------------------|------------------------------|------------------------------|
| Loại cơ sở dữ liệu        | NoSQL, document-based         | NoSQL, document-based        | NoSQL, realtime DB           |
| Đồng bộ đa hướng          | Có (master-master)            | Hạn chế                       | Có (client-based sync)       |
| Truy vấn dữ liệu          | Mango Query                   | Rich query support           | Hạn chế (theo key/path)      |
| Offline-first            | Có                            | Hạn chế                       | Có                           |
| REST API                 | Có                            | Có                           | Có                           |

## 6. Ứng dụng của thư viện  
- **Ứng dụng di động offline-first**: CouchDB hỗ trợ đồng bộ dữ liệu khi thiết bị có kết nối mạng trở lại.  
- **Hệ thống phân tán**: Phù hợp cho các hệ thống cần nhiều máy chủ ghi dữ liệu cùng lúc.  
- **Ứng dụng IoT**: Ghi nhận dữ liệu cảm biến tại các điểm biên và đồng bộ về máy chủ trung tâm.  
- **Hệ thống tài liệu phi cấu trúc**: Quản lý các hồ sơ, biểu mẫu hoặc tài liệu JSON không có cấu trúc cố định.

---

# Đề xuất đề tài: Ứng dụng Quản Lý Ghi Chú Cá Nhân Đồng Bộ với CouchDB

## 1. Giới thiệu  
Trong thời đại số, người dùng cần ghi chú và lưu trữ thông tin cá nhân mọi lúc mọi nơi. Đề tài này xây dựng ứng dụng ghi chú đơn giản, cho phép lưu trữ dữ liệu cục bộ và đồng bộ với CouchDB khi có kết nối.

## 2. Vấn đề cần giải quyết  
Người dùng thường ghi chú trên điện thoại, máy tính bảng hoặc máy tính, nhưng thiếu công cụ đơn giản để đồng bộ giữa các thiết bị mà vẫn hoạt động offline. Đề tài này hướng đến một giải pháp offline-first sử dụng CouchDB.

## 3. Mục tiêu  
- Cho phép người dùng tạo, chỉnh sửa và xoá ghi chú cá nhân.  
- Lưu trữ ghi chú ở dạng JSON trên CouchDB.  
- Đồng bộ dữ liệu giữa các thiết bị khi có kết nối mạng.  
- Giao diện đơn giản, dễ sử dụng.

## 4. Phạm vi  
- Ghi chú bao gồm tiêu đề, nội dung, thời gian tạo.  
- Sử dụng CouchDB làm backend lưu trữ dữ liệu.  
- Tích hợp đồng bộ hóa giữa nhiều client.  
- Xây dựng ứng dụng web hoặc mobile đơn giản (Svelte, React Native…).

## 5. Công nghệ sử dụng  
- **CouchDB**: Lưu trữ và đồng bộ dữ liệu JSON.  
- **PouchDB** (frontend): Lưu trữ local và đồng bộ với CouchDB server.  
- **SvelteKit**: Xây dựng giao diện người dùng.  
- **REST API**: Giao tiếp giữa client và server.

## 6. Kỳ vọng kết quả  
- Ứng dụng có thể chạy offline và đồng bộ khi có mạng.  
- Giao diện thân thiện để tạo và xem ghi chú.  
- Dữ liệu được lưu trữ an toàn, có thể truy cập từ nhiều thiết bị.

