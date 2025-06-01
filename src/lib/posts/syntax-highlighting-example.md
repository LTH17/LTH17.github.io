<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Deliverable 4 – Website</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #FFFBEA;
      color: #333;
      margin: 40px;
      line-height: 1.6;
    }

    h1 {
      color: #1E90FF;
      font-size: 2.5rem;
    }

    .subheader {
      color: #1E90FF;
      font-size: 2rem;
      font-weight: bold;
      margin-top: 40px;
      margin-bottom: 10px;
    }

    .meta {
      font-size: 0.9rem;
      margin-bottom: 20px;
    }

    .divider {
      border-bottom: 2px solid #ccc;
      margin: 30px 0;
    }

    h2 {
      color: #1E90FF;
      font-size: 1.5rem;
      margin-top: 30px;
    }

    code {
      background-color: #f4f4f4;
      padding: 2px 6px;
      border-radius: 4px;
      font-size: 0.95rem;
      color: #0070f3;
    }

    strong {
      font-weight: bold;
    }

    .highlight {
      background-color: #e6f7ff;
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 30px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }

    th, td {
      padding: 12px;
      text-align: left;
      border-bottom: 1px solid #ccc;
    }

    td:first-child {
      font-weight: bold;
    }

    .check {
      color: green;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <h1>DELIVERABLE 4 – WEBSITE</h1>
  <div class="meta">
    <strong>Published:</strong> 2025-06-02<br>
    <strong>Updated:</strong> 2025-06-01
  </div>

  <div class="divider"></div>

  <div class="subheader">Đánh giá hệ thống quản lý phòng khám da liễu</div>

  <p>
    Hệ thống quản lý phòng khám da liễu được xây dựng trên nền tảng <strong>Laravel</strong> và <strong>CockroachDB</strong>, triển khai theo kiến trúc phân tán.
    Dưới đây là báo cáo tổng hợp đánh giá hệ thống theo các tiêu chí của Deliverable 4 trong môn học “Ứng dụng Phân tán”.
  </p>

  <!-- 1.1 -->
  <div class="highlight">
    <h2>1.1. Fault Tolerance (Khả năng chịu lỗi)</h2>
    <p>
      Laravel có thể xử lý lỗi kết nối CSDL thông qua cơ chế exception. Khi CockroachDB bị ngắt, hệ thống hiển thị thông báo lỗi, ghi log và vẫn giữ trạng thái ứng dụng ổn định. CockroachDB hỗ trợ tự động retry và phục hồi khi node trở lại, đảm bảo tính sẵn sàng cao.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 1.2 -->
  <div class="highlight">
    <h2>1.2. Distributed Communication (Giao tiếp phân tán)</h2>
    <p>
      Laravel kết nối tới CockroachDB qua giao thức SQL trên TCP/IP, hỗ trợ truyền thông phân tán đến nhiều node. Việc truy cập CSDL được xử lý phân tán và độc lập giữa các tiến trình.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 1.3 -->
  <div class="highlight">
    <h2>1.3. Sharding hoặc Replication</h2>
    <p>
      CockroachDB phân mảnh dữ liệu tự động và replication trên nhiều node theo mặc định. Laravel không cần thay đổi logic để tận dụng tính năng này. CSDL luôn có bản sao sẵn sàng trên các node khác khi có sự cố.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 1.4 -->
  <div class="highlight">
    <h2>1.4. Simple Monitoring / Logging</h2>
    <p>
      Hệ thống sử dụng Laravel để ghi log các hành vi ứng dụng vào <code>storage/logs/laravel.log</code>. Ngoài ra, CockroachDB cung cấp giao diện Admin UI tại cổng 8080 để theo dõi số lượng node, trạng thái replication, thời gian phản hồi và các truy vấn chậm.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 1.5 -->
  <div class="highlight">
    <h2>1.5. Basic Stress Test</h2>
    <p>
      Đã tiến hành kiểm thử tải bằng cách gửi hàng trăm yêu cầu POST và GET tới các route như <code>/appointments</code>, <code>/doctors</code>, và <code>/invoices</code>. Công cụ sử dụng gồm Apache Bench và Postman Runner. Hệ thống phản hồi ổn định, không ghi nhận lỗi 500, thời gian phản hồi trung bình ở mức chấp nhận được.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 2.1 -->
  <div class="highlight">
    <h2>2.1. System Recovery (Khả năng tự khôi phục)</h2>
    <p>
      CockroachDB hỗ trợ phục hồi tự động từ node khác khi node chính gặp lỗi. Laravel có thể reconnect khi database sẵn sàng. Việc backup được hỗ trợ qua lệnh SQL hoặc công cụ Cockroach CLI.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 2.2 -->
  <div class="highlight">
    <h2>2.2. Leader Election</h2>
    <p>
      Trong cụm CockroachDB, leader election được thực hiện tự động để chọn node xử lý chính cho mỗi shard dữ liệu. Laravel không cần can thiệp vào quy trình này, đảm bảo tính sẵn sàng.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 2.3 -->
  <div class="highlight">
    <h2>2.3. Load Balancing</h2>
    <p>
      Hệ thống có thể triển khai CockroachDB nhiều node và sử dụng proxy như HAProxy hoặc Caddy để phân tải kết nối. Laravel hỗ trợ cấu hình nhiều database host cho failover và balancing.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 2.4 -->
  <div class="highlight">
    <h2>2.4. Consistency Guarantees</h2>
    <p>
      CockroachDB đảm bảo consistency theo chuẩn serializable isolation. Tất cả transaction đều thực hiện đúng thứ tự, không ghi đè và có kiểm soát xung đột. Laravel sử dụng query builder hoặc transaction đảm bảo dữ liệu luôn nhất quán.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- 2.5 -->
  <div class="highlight">
    <h2>2.5. Security Features</h2>
    <p>
      Laravel sử dụng bcrypt để mã hóa mật khẩu và CSRF token cho các form POST. Hệ thống xác thực người dùng qua session hoặc JWT. CockroachDB hỗ trợ TLS và xác thực truy cập qua user role.
    </p>
    <p><strong>Kết luận:</strong> Đạt.</p>
  </div>

  <!-- Tổng kết -->
  <div class="divider"></div>
  <div class="subheader">3. Tổng kết</div>

  <table>
    <tr><th>Tiêu chí</th><th>Đánh giá</th></tr>
    <tr><td>Fault Tolerance</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Distributed Communication</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Sharding/Replication</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Monitoring/Logging</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Stress Test</td><td class="check">✅ Đạt</td></tr>
    <tr><td>System Recovery</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Leader Election</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Load Balancing</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Consistency Guarantees</td><td class="check">✅ Đạt</td></tr>
    <tr><td>Security Features</td><td class="check">✅ Đạt</td></tr>
  </table>

  <p style="margin-top: 20px;">
    Hệ thống quản lý phòng khám da liễu triển khai trên Laravel và CockroachDB đã đáp ứng đầy đủ các yêu cầu của một hệ thống phân tán cơ bản, sẵn sàng mở rộng và tích hợp thêm tính năng nâng cao trong tương lai.
  </p>

</body>
</html>
