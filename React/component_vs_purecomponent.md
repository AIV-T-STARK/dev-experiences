### ♳ TỔNG QUAN
  > *Bài này sẽ nói cụ thể và demo cụ thể sự khác nhau giữa hai thằng React.Component và React.PureComponent.
  > Chắc không ít bạn cũng đã từng bị phỏng vấn câu này rồi, nhưng không ít bạn trả lời theo kiểu lý thuyết.
  > OK mình sẽ giúp các bạn hiểu sâu hơn một chút.*

**☞ Tóm lại thì 2 thằng này khác nhau ở một số điểm sau:**
1. *React.Component cho phép dev override lại shouldComponentUpdate hook, mặc định hook này reference compare để quyết định re-render lại hay không.*
2. *React.PureComponent không cho phép dev overide lại shouldComponentUpdate hook, nếu bạn cố tình overide thì bạn sẽ ăn ngay warning. Hook này shallow compare để quyết định re-render lại hay không.*
3. *Đôi khi nếu thấy Component render chậm, hãy thử set shouldComponentUpdate hook return true hoặc return false.*
```
class Demo extends React.Component {
  ...
  shouldComponentUpdate() {
    return true; // Props|State thay đổi thì re-render luôn. Không cần compare nữa!
    // return false; // Sẽ chặn không bao giờ cho Component re-render. Render HTML tĩnh.
  }
  ...
}
 ```
----
### ♴ NỘI DUNG
  > *Để mình lấy một ví dụ đơn giản nhất, trước khi đọc bài này có lẽ bạn nên đọc một chút về lifecycle hook.
  >> https://github.com/nguyenvanhoang26041994/dev-experiences/blob/master/React/lifecycle_hook*

`☞ Step 1:`
### ♵ CHIA SẼ THÊM