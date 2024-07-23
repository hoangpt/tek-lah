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

