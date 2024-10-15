# Frontend Tests

### B là 1 lập trình viên FE. Anh ấy muốn viết kiểm thử cho function add(x,y)

```javascript
// Javascript
function add(x, y) {
  return x + y;
}
```

Và đây sẽ là đoạn code test với sự trợ giúp của Copilot

```javascript
// Sử dụng assert lib
const assert = require('assert');

describe('add function', () => {
  it('should add two numbers positive correctly', () => {
    assert.equal(add(2, 3), 5);
  });
  
  it('should add two numbers negative correctly', () => {
    assert.equal(add(-2, -3), -5);
  });
 
});
```

### Bài tập:

Bài 1: Viết unittest cho function tính phép nhân

Bài 2: Sử dụng Copilot để tạo testcase cho các trường hợp biên, ví dụ null, undefined value, hoặc giá trị quá lớn như .1\*E1.000.000.000

Bài 3: Lấy 1 dự án đơn giản nào đó. Xem các đoạn code thiếu testing script và hoàn thiện nó dùng Copilot.

### Ngẫm:

* Làm sao đảm bảo các test đủ cover hết các khả năng.
* Câu prompt nào bạn đưa ra để Copilot bổ sung thêm các testscript còn ghiếu.
* LIệu Copilot có hỗ trợ các loại test khác không: e2e, integration, feature. Bạn thử dùng copilot viết những loại này xem.
