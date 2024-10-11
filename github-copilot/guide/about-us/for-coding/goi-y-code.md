# Gợi ý code

## Mô tả

{% hint style="info" %}
**Concept:** Một trong những tính năng chính của Copilot là code cùng. Khi chúng ta gõ tên functions, hoặc comments (là 1 dạng prompting inline) thì copilot sẽ đưa ra các gợi ý code dưới dạng chữ mờ (ghost text).
{% endhint %}

## **Ví dụ:**

_Input Code_

```javascript
function calculateSum(a, b) {
    // Enter your code here
}
```

_Result Suggested by Copilot_

```javascript
function calculateSum(a, b) {
    // Enter your code here
    const sum = a + b;
    return sum;
}
```

## Bài tập:

* **Bài 1**: Hoàn thiện `calculateSum(a, b)` sử dụng GitHub Copilot's suggestions. Thử với các ngôn ngữ khác và khám phá Copilot hướng dẫn chúng ta như nào.
* **Bài 2**: Sử dụng Copilot để viết `calculateProduct(a,b)`  và viết chạy thử cho các phép nhân với các cặp khác nhau như (1,2), (-1, 9), (1.000.000, 20.000.000.000).
* **Bài 3**: Thử expose 2 api này qua web.  &#x20;

## Ngẫm?

* Copilot có gen code đúng như chúng ta mong muốn?
* Copilot có xử lý error chưa (đầu vào, tràn bộ nhớ)? Nếu chưa, thử comment hoặc gõ các chữ đầu để Copilot sửa?
* Cần phải viết comment hoặc cung cấp context như nào để copilot hiểu tốt hơn?
