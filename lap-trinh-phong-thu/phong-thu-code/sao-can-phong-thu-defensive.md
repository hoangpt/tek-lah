# 💡 Sao cần Phòng thủ (Defensive) ?

{% hint style="info" %}
**Tinh gọn:** DF cần vì trong 1 app lớn đều sử dụng các libs ngoài, và sử dụng chéo giữa các module với nhau. Nếu không có DF, nhất là trong các ứng dụng liên quan tới tiền, 1 số lỗi có thể có như crash\_app, transaction không hoàn tất, dữ liệu bị "orphan", bị bad dẫn tới mất tiền, tiền tự sinh. DF nghĩa là chúng ta protect code của mình và đé ...o tin code thằng nào hết.
{% endhint %}

## Chém gió:

BR: anh vừa nghe bên chú vừa có phốt to ah? Nghe nói phải bồi thường cho 1 công ty vì không  check kỹ điều kiện transaction.

LC: đúng rồi anh. Nhọ vãi nồi. Hôm T5 team em dính thì T6 em nghe Crowstrike và Microsoft dính. Thế vẫn may đại ca ah, đến team lớn nó còn lởm vậy.

BR: ờ, thôi thì rút kinh nghiệm. Nói chung may không đổ nhà đổ cửa chết người. Chứ nhiều vụ, phần mềm lởm dẫn tới chết người như vụ của Boeing ấy. Mấy lỗi này nếu hiểu về kỹ thuật Defensive Programming thì có thể hạn chế nhiều đó.

```
// boeing và lỗi phần mềm
let url = "https://vtv.vn/loi-phan-mem-may-bay.html"
url.plane_crash()
```

LC: em mới nghe cái này lần đầu. Đại ca giải thích thêm xem nào

BR: thực ra thì chú cũng áp dụng nhiều trong code đó, nhưng có thể mới chỉ 1 phần nào đó. Ví dụ như việc **check null, xử lý các exception**.&#x20;

LC: vâng

BR: nhưng nếu nói về khái niệm thì nó là 1 từ vay mượn từ ngành giao thông. Giả sử mày là tài xế, thì mục tiêu cao nhất là gì nào?

LC: thì là lái xe an toàn về nhà ... xem tivi, chơi game, xếp hình với vk.

BR: Ờ, thế những cái gì ảnh hưởng tới việc lái xe của chú?

LC: Thì em lái ngon, lái cẩn thận.

BR: Ờ, chưa đủ. Chú còn phải care các thằng khác nữa. Chú lại ngon, nhưng thằng khác lái ẩu, đâm mẹ vào đít chú ... thì có đau không

LC: Đúng anh.

BR: Đó, cũng như vậy Defensive Programming là **cách code mà mình đé....o tin code thằng nào hết**. Bố mày validate hết mọi thứ để đảm bảo dữ liệu an toàn. Cái này giống như hành khách, hàng của chú. Thằng ngu, thằng khôn, hàng thường, mai thuý ... kiểm tra trước khi vận chuyển.

Thứ nữa là, nếu dùng libs ngoài, hay dùng chéo các module khác, ... cũng không nên tin 100%. Nên có handle exception ngoài cùng để nếu có exception xẩy ra, mình vẫn bẫy được và không bị crash\_app.

LC: như vậy thì sẽ không bao giờ lỗi đúng không đại ca.

BR: giảm thiểu thôi. Chứ libs của nó méo throws ra exception thì chú bẫy kiểu giè. Thế nên mới có 1 vài kỹ thuật khác như **Assert lúc Runtime**, ...&#x20;

Hơn nữa, thủ lắm quá nó dẫn tới "méo biết ghi bàn". Thôi mai để anh làm tý guide docs cho chú đọc và thực hành nhé. "Bí kíp công thủ toàn diện", chứ hết mịa giờ ra chơi roài.

LC: dạ, chào đại ca về nhà xếp hình với vk an toàn he ^^

