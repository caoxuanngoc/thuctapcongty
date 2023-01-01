# Tuần 3 ngày 2:
1. Chủ đề kiến thức đã tìm hiểu trong ngày
  - NgRx
    + @ngrx/store
    + @ngrx/effects
2. Công việc/hoạt động đã làm trong ngày
  - Đọc tài liệu về @ngrx/store
  - Đọc tài liệu về @ngrx/effects
  - Thực hành xây dựng chức năng đăng nhập user với @ngrx/store và @ngrx/effects
3. Điều tìm hiểu được 
  - Những State nào nên để vào Store?
    + Những State nào cần share giữa các Component với nhau.
    + Những State nào cần phải Hydrated: Quá trình object biến thành string, và string biến thành object
    + Những State nào cần chia sẽ giữa các route (made Available across routes)
    + Những State nào lấy được từ server (Retrieved with a side effect) 
    + Những State nào bị ảnh hưởng bởi components/effects khác thuộc về Store
  - Giới thiệu về NgRx và cách cài đặt: https://viblo.asia/p/ngrx-la-gi-thu-nghiem-voi-ngrx-trong-ung-dung-angular-phan-1-djeZ1pVjKWz
  - Thử nghiệm với NgRx trong ứng dụng Angular - Xây dựng chức năng Auth: https://mherman.org/blog/authentication-in-angular-with-ngrx/