# Khảo sát chất lượng giảng dạy

Ứng dụng Streamlit tiếng Việt để sinh viên đánh giá chất lượng giảng dạy ẩn danh và nhà quản lý theo dõi kết quả.

## Cài đặt và chạy

Yêu cầu Python 3.10 trở lên.

1. Mở PowerShell tại thư mục chứa ứng dụng.
2. Cài các thư viện cần thiết:

   ```powershell
   python -m pip install -r requirements.txt
   ```

3. Chạy ứng dụng:

   ```powershell
   python -m streamlit run app.py
   ```

4. Mở địa chỉ được hiển thị trong PowerShell. Lần đầu vào mục **Nhà quản lý**, tạo mật khẩu tối thiểu 10 ký tự.
5. Tạo khảo sát và các tiêu chí ở mục **Tạo khảo sát**, sau đó gửi địa chỉ ứng dụng cho sinh viên.

## Sử dụng

- **Sinh viên:** chọn một khảo sát đang mở, chấm điểm từng tiêu chí từ 1 đến 5, thêm góp ý nếu muốn rồi gửi. Không cần đăng nhập.
- **Nhà quản lý:** đăng nhập bằng mật khẩu đã tạo; tạo khảo sát, mở/đóng hoặc xóa khảo sát; xem điểm trung bình, biểu đồ và góp ý; tải dữ liệu khảo sát dưới dạng CSV.
- Khi xóa khảo sát, toàn bộ điểm và góp ý thuộc khảo sát đó cũng bị xóa.

## Chia sẻ ứng dụng

Để người khác truy cập, triển khai ứng dụng trên máy chủ hoặc dịch vụ lưu trữ có thể truy cập từ mạng của họ. Khi chạy trên máy chủ trong mạng nội bộ, có thể mở địa chỉ mạng bằng lệnh:

```powershell
python -m streamlit run app.py --server.address 0.0.0.0
```

Sau đó chia sẻ địa chỉ mạng của máy chủ. Chỉ chia sẻ mật khẩu quản lý với những người được phép xem kết quả. Nếu đưa ứng dụng lên Internet, hãy dùng kết nối HTTPS và bảo vệ máy chủ cũng như tệp dữ liệu.

## Dữ liệu và quyền riêng tư

- Dữ liệu khảo sát được lưu trong cơ sở dữ liệu SQLite `surveys.db` tại thư mục chạy ứng dụng. Đặt biến môi trường `SURVEY_DATABASE_PATH` để chọn vị trí lưu khác.
- Mật khẩu quản lý được lưu dưới dạng băm có muối; ứng dụng không lưu tên hoặc email của sinh viên.
- Ứng dụng lưu thời gian gửi phản hồi để phục vụ báo cáo. Nhà cung cấp máy chủ hoặc proxy có thể có nhật ký truy cập riêng; không thu thập thông tin nhạy cảm trong phần góp ý.
- Dùng ổ đĩa bền vững và sao lưu `surveys.db` khi triển khai. SQLite cục bộ phù hợp cho một bản chạy ứng dụng; nhiều bản sao chạy đồng thời cần dùng dịch vụ lưu trữ dữ liệu dùng chung.
