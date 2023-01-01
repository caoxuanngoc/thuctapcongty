# Tuần 5 ngày 2:
1. Chủ đề kiến thức đã tìm hiểu trong ngày
  - Animation
  - NgZone
2. Công việc/hoạt động đã làm trong ngày
  - Đọc tài liệu về Angular Animations
  - Đọc tài liệu về NgZone
  - Xem video về Change Dectection trong Angular
  - Thực hành tạo animation với Angular Animations
  - Thực hành NgZone giúp tối ưu hiệu năng của angular application
3. Điều tìm hiểu được 
  - Chúng ta không thể giải quyết mọi vấn đề với CSS animation vì bạn cần kết hợp logic Javascript với CSS animation. Trong Angular chúng ta có thể làm điều đó với BrowserAnimationsModule. Angular Animations cung cấp cho chúng ta các function như: trigger, transition, animate, states, ... đề tạo animation. Ngoài ra còn có các từ khóa như:  enter, leave, void và các state trong Angular animations.
    + Chúng ta cần import { BrowserAnimationsModule } from '@angular/platform-browser/animations' vào app.module để có thể sử dụng Angular animation
    + Tài liệu Animation transitions and triggers: https://angular.io/guide/transition-and-triggers
  - NgZone có thể giúp thực thi mã của chúng ta ở ngoài Angular Zone, điều này sẽ ngăn không cho Angular thực thi những task phát hiện được cho là không cần thiết, qua đó giúp tăng hiệu năng của ứng dụng.
    + Khi chúng ta thêm {ngZone: 'noop'} vào platformBrowserDynamic().bootstrapModule() ở main.ts thì Angular sẽ không nhận biết các sự thay đổi (change detection) trong các component của chúng ta -> không tự động cập nhật lại giao diện.
    + Để chạy code của chúng ta ở bên ngoài Angular's Zone chúng ta sử dụng: NgZone.runOutsideAngular() -> code sẽ được chạy ngầm bên dưới mà không ảnh hưởng đến giao diện HTML của chúng ta
    + Chúng ta sử dụng NgZone.run() bên trong NgZone.runOutsideAngular() (với điều kiện nào đó) để có thể chạy lại code của chúng ta trong Angular's Zone -> lúc này phần giao diện HTML của chúng ta sẽ tự động cập nhật theo dữ liệu được binding như bình thường.