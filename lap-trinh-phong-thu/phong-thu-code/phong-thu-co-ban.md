# ✨ Phòng thủ cơ bản?

{% hint style="info" %}
**Tinh gọn:** Một số concept về phòng thủ: không nên work around khi có defect, sử dụng fail fast hơn fail safe, hướng tới compile err hơn runtime err, dead app không biết nói dối.

Một số kỹ thuật phổ biến:

* Compile check (validation kỹ)
* Assertion (runtime check)
* Dùng tool/bots review và check, phân tích code bốc mùi.
{% endhint %}

## Chém gió

LC: đại ca, hôm qua bảo có guide cho em về cách phòng thủ. Thế hôm nay anh có chưa?

BR: anh quên moẹ rồi. Thôi, mình hand-on vậy. Chú biết là nếu không thủ thì khả năng bị ghi bàn rất cao. Bản chất của lập trình thì .. tới 90% là viết code validation để thủ với bọn hacker và với bọn người dùng "ngoo", ngáo.

LC: He

BR: giả sử đây là màn hình đăng nhập nhé. Có 1 ô input ghi là nhập username, bọn khôn nó nhập đúng. Còn bọn "ngoo" nó nhập "Bình Ruồi", còn bọn hacker nó nhập "\<script>?!#INSERT INTO\</script>". Và thế là bùm, bọn ngoo sẽ chởi mình là app như lìn, còn bọn hacker thì ghi được vào DB của mình acc admin và đọc hết data, bao gồm cả tiền của khách.

Rồi nó lấy tiền đó đi tiêu, còn chúng ta phải đền. Mà đé ...o phải bọn PM, CEO đền đâu. Hệ thống lỗi nó lôi anh em dev ra chửi ngoo, rồi anh em mình đền và bị sa thải. Như vụ crowstrike, cả thế giới nó chửi thằng code chứ có chửi con BA, thằng QC hay bố PM bỏ mẹ nào đâu. Trong khi lỗi này do con BA không define đủ case, thằng QC đé...o liệt kê được bad case, rồi PM thì không UAT tốt trên môi trường beta/alpha.

LC: đại ca đã nói đúng ... lại còn nói to.

BR: he. Thế nên là dev, chú phải thay đổi tư duy. Nếu kiếm được solution nào không code là tốt nhất, vì nó "battle test" với nhiều khách hàng. Còn nếu phải code, phải đặt mình như User, như QC và cả BA nữa. Thậm chí là hacker.

### Guide 1: Viết function, API validate mọi required params

BR: cái này thì khá dễ hiểu. Nó là case màn hình input kia kìa. Nhưng mở rộng hơn sang API, function nhé. Bản chất chúng ta viết API, Function là cho các bạn dev khác dùng. Nhưng dev cũng có dev that, dev this ... he, nên đé...o tin ông nào hết.

```java
// function / api check required params (JAVA Demo_
public function createUser(String username, String password, String[] options){
    if (username == null || username.equals("")){
        throw new Exception("Ngoo. Why garbage here?");
    }
    if (password == null || password.equals("")){
        throw new Exception("Hacked me? Cut.");
    }
    
     // .... continue logic
}
```

Cái này dẫn tới 1 cái guide rất hay là, càng ít params required càng ít, càng expose ít function càng tốt

### Guide 2: Public functions và required params càng ít càng tốt

BR: Cái này dựa trên lý thuyết, ai cũng "ngoo" nên khi làm API/Function cho bọn khác gọi, càng đơn giản càng tốt. Hãy suy nghĩ như người làm dịch vụ, problem là của tao, còn mày làm giải pháp. Chứ không phải bọn tao dùng 1 sản phẩm ... như bãi rác và đé...o biết dùng sao.

Trong Java, có thể dùng các khái niệm private function (chỉ 1 hoặc 2 functions mình cho dev khác dùng), farcase, module interface, ... Default value cho các params optional là các value cơ bản nhất, chấp nhận cả null.

LC: oh, em tưởng null phải chekc.

BR: chú nhầm. Nhiều business, null cũng là 1 giá trị, không cần set. Như trong db, function đó ghi vào db fullName của user là null. Nghĩa là tạm thời user đó không cung cấp fullName thoai.

BR: nói chung, coding chú hiểu là abstract wrapper nên ít thì đỡ maintain nhiều, và nó cũng có 1 cái rất hay là, kỹ thuật tấn công, tránh thủ mọi nơi overly defensive.

### Guide 3: Exception

