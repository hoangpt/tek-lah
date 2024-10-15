# Kết hợp unitest và feature test

### Ví dụ:

Bạn T có 1 function tính tổng giá tiền 1 shoping card, và bạn muốn refactor để dễ hiểu hơn

```python
def total_price(items):
    return sum(item['price'] * item['quantity'] for item in items)
```

Trước khi refactor, tests được copilot viết để đảm bảo luôn đúng

```python
def test_total_price():
    items = [
        {'price': 5, 'quantity': 2},
        {'price': 3, 'quantity': 1}
    ]
    assert total_price(items) == 13
```

Có thể yêu cầu copilot viết lại sử dụng for cho dễ hiểu. Dùng câu lệnh /fix

```python
def total_price(items):
    total = 0
    for item in items:
        total += item['price'] * item['quantity']
    return total
```

Tests vẫn ok, nên việc refactor là đảm bảo.
