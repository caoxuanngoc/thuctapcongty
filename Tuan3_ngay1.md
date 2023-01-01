# Tuần 3 ngày 1:
1. Chủ đề kiến thức đã tìm hiểu trong ngày
  - RxJS
2. Công việc/hoạt động đã làm trong ngày
  - Đọc tài liệu so sánh sự khác nhau giữa Promise và Observable
  - Đọc tài liệu và thực hành chạy thử các operator trong RxJS
3. Điều tìm hiểu được 
  * Phân biệt các operator mergeAll(), concatAll(), switchAll() vaf exhaustAll()
  - Các operator trên giúp chuyển Higher Order Observables về lại thành First Order Observable, tránh trường hợp subscribe lồng nhau.
    vd: hoo$.subscribe((obs) => {
	   obs.subscribe(console.log); // in subscribe
	});
    + Higher Order Observables là các Observable (Outer Observable) sẽ return ra Observable (Inner Observable) khác.
      vd: // Observable<Observable>
	  const hoo$ = interval(1000).pipe( //Outer Observable (parent Observable)
  			map((val) => of(`I am at: ${val}`)) // Inner Observable (child Observable )
		      );
    + First Order Observable là các Obs return về các giá trị kiểu array, object, number, string, ....
      vd: // Observable<string>
	  const foo$ = interval(1000).pipe(
  			map((val) => `I am at: ${val}`)
		      );
  - Hiểu đơn giản các operator trên sẽ subscribe các inner Obs, xong rồi trả về giá trị cho outer Obs.
  - Ví dụ mẫu cho các operator trên:
    fromEvent(document, 'click').pipe(
  	map(() => interval(1000).pipe(take(5))),
 	mergeAll()
    );
  - mergeAll()
    => Có bao nhiêu inner Obs chạy bấy nhiêu inner Obs (chạy song song nhau)
    => Nó có 1 đối số là concurrent: number -> chỉ ra số inner obs tại 1 thời điểm có thể chạy song song, khi số obs này complete thì số obs còn lại sẽ tiếp tục quy trình.
  - concatAll()
    => Chạy tuần tự các inner Obs, Obs nào complete thì chạy Obs tiếp theo
    => Tương tự mergeAll(1) (đối số concurrent là 1)
  - switchAll()
    => Ví dụ có 2 inner Obs
    ==> 1 Obs đang chạy nhưng chưa complete
    ==> thì 1 Obs khác được invoke -> thì Obs thứ nhất sẽ bị unsubcribe và Obs thứ 2 này sẽ được chạy.
  - exhaustAll()
    => Trong khoảng thời gian mà 1 Obs đang chạy, thì tất cả các Obs khác sẽ bị cancel
    => Ví dụ có 3 inner Obs
    => Thì chỉ có 1 Obs đầu tiên chạy, 2 Obs còn lại đã bị cancel.
  - Như ví dụ mẫu ở trên, chúng ta phải dùng map() rồi dùng mergeAll(). RxJS có sẵn các operator giúp code ngắn gọn hơn
    => mergeMap() = map() + mergeAll()
    => concatMap() = map() + concatAll()
    => switchMap() = map() + switchMap()
    => exhaustMap() = map() + exhaustMap()
    => Khuyên dùng những operator này.
  - Bài so sánh Promise và Observable: https://www.syncfusion.com/blogs/post/angular-promises-versus-observables.aspx