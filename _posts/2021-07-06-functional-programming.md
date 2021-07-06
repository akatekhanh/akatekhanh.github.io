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


Như vậy các bạn đã hiểu tại sao gọi là hàm lambda là gì và tại sao lại gọi là hàm lambda. Vậy hàm lambda dùng để làm gì ? Một số trường hợp ta nên sử dụng lambda function như sau:
- Khi ta muốn sử dụng hàm một lần, với ít tham số và ít các phát biểu (statements).
- Dễ hiểu logic và trực quan, giúp code dễ đọc hơn.

## Hàm bậc cao: map, filter, reduce

Hàm bậc cao trong Python nói riêng và trong Khoa học máy tính nói chung gồm một số đặc điểm sau:
    - Tham số nhận vào là một hàm hoặc một danh sách hàm.
    - Kết quả trả về là một hàm.

Một số hàm bậc cao được tích hợp sẵn trong Python gồm **map(), filte(), reduce()**. Vì hàm bậc cao nhận đối số vào là 1 chuỗi tham số là các hàm nên hàm vô danh Lambda được sử dụng tốt nhất với các hàm này.

### Map() function

Syntax function:

```python
map(<function>, <sequence>): <function> lấy mỗi phần tử trong chuỗi <sequence> và trả về một trình lặp.
```

Nghe hơi khó hiểu ha, mình sẽ lấy một vài ví dụ. _Giả sử chúng ta có 1 list các number, và ta đang muốn nhân từng số đó với 100_. 

```python
list_number = [1, 2, 3, 4, 5]
new_list_number = list(map(lambda: number, number * 100), list_number)
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