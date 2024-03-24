---
layout: post 
title: 4. Hàm vô danh (lambda function) và hàm bậc cao (high-oder function).
subtitle: Hàm vô danh là gì? Hàm bậc cao là gì? Sau bài viết này mình hi vọng chúng ta sẽ hiểu được những chủ đề nâng cao này trong python.
tags: [Python cơ bản]
cover-img: /assets/img/3.data-structure/img-1.jpeg
comments: true
---

## Hàm Lambda trong Python.

Trong Python, hàm vô danh được định nghĩa là hàm không có tên hàm. Hàm thông thường trong python có syntax như sau: 

```python 
def function_name(parameters):
    statements(s)
```
**function_name** là bắt buộc phải có. Tuy nhiên hàm lambda thì lại khác, nó là một hàm mà không cần **function_name**, và hàm lambda được định nghĩa bằng cách sử dụng từ khoá **lambda**, chính vì thế nên nó được gọi là hàm Lambda hay hàm vô danh. Ví dụ:

```python
lambda a,b : a + b

# call function
(lambda a, b : a + b)(10, 20)
# output: 30

# another example
test_lambda = lambda a,b : a * b
test_lambda(5, 10)
# output: 50
```

Syntax lambda function (mình sử dụng syntax tổng quát)
lambda (<param>(, <param>)*)? : <expression>
{: .box-note}


Vậy hàm lambda dùng để làm gì ? Một số trường hợp ta nên sử dụng lambda function như sau:
- Khi ta muốn sử dụng hàm một lần, với ít tham số và ít các phát biểu (statements).
- Dễ hiểu logic và trực quan, giúp code dễ đọc hơn.

## Hàm bậc cao: map, filter, reduce

Hàm bậc cao trong Python nói riêng và trong Khoa học máy tính nói chung là hàm nhận tham số là một hàm khác và trả về một hàm (Higher order functions). Một số tính chất của hàm bậc cao: 
- Tham số nhận vào là một hàm hoặc một danh sách hàm.
- Kết quả trả về là một hàm.

Một số hàm bậc cao được tích hợp sẵn trong Python gồm **map(), filte(), reduce()**. Vì hàm bậc cao nhận đối số vào là 1 chuỗi tham số là các hàm nên hàm vô danh Lambda được sử dụng tốt nhất với các hàm này.

### Map() function

Syntax function:
```python
map(<function>, <sequence>)

<function>: Tham số đầu tiên của hàm _map()_ là một hàm khác (callable), hoặc có thể là một hàm Lambda.
<sequence>: Là một iterator. Ví dụ như List, set, tuple hoặc là một iterator.
```

_Giả sử chúng ta có 1 list các number, và ta đang muốn nhân từng số đó với 100_. 

```python
list_number = [1, 2, 3, 4, 5]
new_list_number = list(map(lambda number: number * 100), list_number)
print(new_list_number)
# [100, 200, 300, 400, 500]


# Hoặc 1 cách tiếp cận khác cho bài toán vừa rồi là dùng list comprehension
new_list_number = [number*100 for number in list_number]
# [100, 200, 300, 400, 500]
```

Một ví dụ khác về cách sử dụng hàm **map()**.

```python
list_1 = [1, 2, 3, 4, 5]
list_2 = [2, 3, 4, 5]
new_list = list(map(lambda item1, item2: item1 + item2, list_1, list_2))
print(new_list)
# [3, 5, 7, 9]
```

### Filter() function
Filter trong Python là hàm dùng để lọc ra các phần tử theo điều kiện của hàm truyền vào. Cú pháp của _filter_ cũng tương tự như hàm _map()_

```python
filter(<function>, <sequence>)

<function>: Tham số đầu tiên của hàm _map()_ là một hàm khác (callable), hoặc có thể là một hàm Lambda.
<sequence>: Là một iterator. Ví dụ như List, set, tuple hoặc là một iterator.
```

Một ví dụ khác về cách sử dụng hàm **map()**.

```python
numbers = [1, 3, 6, 9, 15]
is_odd = filter((lambda number: number%2==1), numbers)
for number in is_odd:
    print(number)
# 1
# 3
# 9
# 15
```

### Reduce() function
![Reduce function](/assets/img/4.higher-function/2022-01-08-21-50-19.png)
Tương tự như _map() và filter()_, reduce() cũng nhận hai tham số đầu vào là một function callale và một sequence. Tuy nhiên _reduce()_ có một vài điểm khác so với _map() và filter()_, thay vì duyệt qua từng phần tử thì reduce sẽ gộp (combine) mỗi hai phần tử trong sequence sau đó đưa vào function của tham số thứ nhất để tính toán. Chúng ta hãy xem xét ví dụ dưới đây:

```python
# Import reduce từ module functools
from functools import reduce
numbers = [1, 2, 3, 5, 8, 13]

def normal_sum(x, y):
    return x + y

# Sử dụng normal_sum như tham số đầu vào của reduce
result = reduce(normal_sum, numbers)

# Hàm reduce sẽ combine từng cặp phần tử trong biến numbers
# đưa vào hàm normal_sum để tính toán, kết quả của lần lặp 
# sẽ tiếp tục được combine với phần tử tiếp theo của biến numbers để tính toán
Output: (((((1+2)+3)+5)+8)+13) = 32
```

```python

```



