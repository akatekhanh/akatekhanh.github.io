---
layout: post 
title: 3.Cấu trúc dữ liệu trong python
subtitle: Sự khác biệt và ứng dụng của các kiểu cấu trúc dữ liệu thông dụng của List, Set, Tuple và Dictionary
tags: [Python cơ bản]
cover-img: /assets/img/3.data-structure/img-1.jpeg
comments: true
---
Chào các bạn, cấu trúc dữ liệu là một phần quan trọng không chỉ của _Python_ mà còn quan trọng ở các ngôn ngữ lập trình khác. Tuy nhiên mỗi kiểu cấu trúc trong từng ngôn ngữ khác nhau lại có những tính chất, đặc trưng khác nhau. Trong nội dung bài viết này mình xin trình bày 4 kiểu cấu trúc dữ liệu quan trọng và cơ bản của _Python_ để người đọc nắm rõ những tính chất và đặc trưng của nó, áp dụng vào những vấn đề của riêng mình.

## Mutable và immutable
Đầu tiên, chúng ta cần làm rõ hai khái niệm hết sức quan trọng trong _Python_ là mutable và immutable và mọi kiểu dữ liệu đều quy về hai loại là **mutable** và **immutable**.

1. Mutable
    - Những đối tượng này có thể thay đổi sau khi khởi tạo.
    - Nhóm dữ liệu này bao gồm **list, set và dict** và các loại kiểu dữ liệu do người dùng định nghĩa (phụ thuộc vào các hành vi do người dùng định nghĩa)

2. Immutable
    - Những đối tượng này hoàn toàn không thể thay đổi sau khi khởi tạo
    - Nhóm dữ liệu này gồm **tuple**, một số kiểu dữ liệu built-in type như **number, string,..** và các loại kiểu dữ liệu do người dùng định nghĩa (phụ thuộc vào các hành vi do người dùng định nghĩa).

Để hiểu hơn về mutable và immutable các bạn có thể tham khảo thêm về bài viết này tại đây.

## List
List là một kiểu dữ liệu cực kì quan trọng trong Python và các ngôn ngữ khác, chúng ta có thể gặp List ở bất kì dự án nào của Python. List là một tập các giá trị bao quanh bởi cặp dấu **[ và ]**, ngăn cách các giá trị và các dấu phẩy(**,**). Mỗi giá trị trong List là bất kì kiểu dữ liệu nào trong Python, kể cả các loại kiểu dữ liệu do người dùng tự định nghĩa.

```python
list_example = [1, 'a', [1, 4, 'abc']]
type(list_example)
#<class 'list'>
```

Các thao tác cơ bản với List: 

**Truy cập tới phần tử trong mảng**: Khi truy cập tới các phần tử trong mảng ta sử dụng **index** để truy xuất, index bắt đầu từ 0

```python
print(list_example[0]) 
# a
print(list_example[2]) 
# [1, 4, 'abc']

Vì List là Mutable nên ta có thể truy xuất từng phần tử của mảng để sửa đổi giá trị

```python
list_example[0] = 'abcedf'
print(list_example)
# ['abcedf', 'a', [1, 4, 'abc']]
```

**Một số thao tác trên List sử dụng các built-in function.**

    - Lấy độ dài của một mảng ta sử dụng hàm **len()**
    ```python
    len(example_list)
    # 3
    ```

    - Thêm phần tử mới vào mảng ta sử dụng **append** để thêm 1 phần tử vào mảng.
    ```python
    example_list.append(123456)
    print(example_list)
    # ['abcedf', 'a', [1, 4, 'abc'], 123456]
    ```

    - Gộp hai mảng ta sử dụng **extend**.
    ```python
    example_list.extend(['e', 'f'])
    print(example_list)
    # ['abcedf', 'a', [1, 4, 'abc'], 'e', 'f']
    ```

    - Sắp xếp 1 mảng dử dụng **sort**.
    ```python
    example_sort = [2, 4, 1, 0, -1]
    example_sort.sort()
    print(example_sort)
    # [-1, 0, 1, 2, 4]
    ```
Ngoài ra bạn có thể tham khảo các phương thức và hàm với List tại [đây](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists).

## Tuple
Cũng như List, Tuple là kiểu dữ liệu mà mỗi phần tử có thể chứa bất kì kiểu dữ liệu nào khác, tuy nhiên sau khi khỏi tạo giá trị thì các phần tử của Tuple không thể thay đổi (List có thể thay đổi). Vì vậy mà Tuple có tốc độ truy xuất cao hơn List. Các phần tử trong Tuple được ngăn các bởi dấu phẩy và được bao bởi cặp ngoặc tròn **( và )**.

```python
example_tuple = (1, 2, ['a,' 'b'], ('c', 'd'))
type(example_tuple)
# <class 'tuple'>
```

**Một số thao tác cần lưu ý khi sử dụng Tuple**
    - Không thể thay đổi phần tử trong Tuple
    - Không thể xoá phần tử trong Tuple

## Set
Set là tập hợp các phần tử duy nhất, nghĩa là trong một Set thì không thể có hai giá trị trùng nhau, khi khai báo hoặc khởi tạo 1 Set có các giá trị trùng nhau thì Python sẽ tự động xoá các phần tử dư thừa chỉ để lại phần tử đầu tiên. Set chứa được bất kì kiểu dữ liệu nào, các phần tử trong Set được ngăn cách nhau bởi dấu phẩy và được bao bởi cặp ngoặc nhọn **{ và }**.

```python
example_set = {1,'a', 'b'}
type(example_set)
# <class 'set'>
```

**Các thao tác cơ bản với Set.**

```python
# Thêm một phần tử vào set
example_set.add(10)
print(example_set)
# {1, 'a', 10, 'b'}

# Xoá phần đầu tiên khỏi set
example_set.pop()
print(example_set)
# {'a', 10, 'b'}
```

**Phép giao, phép hợp, phép bù và phép trừ với Set.**

```python
example_set_1 = {1, 2, 3, 4}
example_set_2 = {3, 4, 5, 6}

# Phép giao (&)
example_set = example_set_1 & example_set_2
print(example_set)
# {3, 4}

# Phép hợp (|)
example_set = example_set_1 | example_set_2
print(example_set)
# {1, 2, 3, 4, 5, 6}

# Phép bù (^)
example_set = example_set_1 ^ example_set_2
print(example_set)
# {1, 2, 5, 6}

# Phép trừ
example_set = example_set_1 - example_set_2
print(example_set)
# {1, 2}
```

Một ứng dụng khác cũng rất hay gặp trong Set là kĩ thuật loại bỏ các phần tử trùng nhau (deduplicate)
```python
example_deduplicate = set([1, 4, 1, 5, 6, 1, 4, 9])
print(example_deduplicate)
# {1, 4, 5, 6, 9}
```

## Dictionary
Dictionary là kiểu dữ liệu lưu giá trị với dạng **key-value**, các key phải có giá trị khác nhau, key **chỉ chấp nhận** các giá trị có kiểu dữ liệu là **string, number, tuple**. Mỗi phần tử trong dict là một cặp key-value, các phần tử cách nhau bởi dấu phẩy, một dict được bao quanh bởi cặp dấu **{ và }**.

```python
example_dict = {
    "item_1": 10,
    2: "abc"
}
type(example_dict)
<class 'dict'>
```

**Một số thao tác cơ bản trên dict**

```python
# Lấy key của dict, return list of keys
keys = example_dict.keys()
print(keys)
# ["item_1", 2]

# Lấy các values của dict
values = example_dict.values()
print(values)
# [10, "abc"]

# Truy cập tới 1 phần tử trong dict 
example_dict["item_1"]
# 10

# Thêm phần tử vào dict
example_dict["item_2"] = 20
print(example_dict)
# {'item_1': 10, 2: 'abc', 'item_2': 20}

# Xoá 1 phần tử khỏi dict
example_dict.pop("item_1")
# {2: 'abc', 'item_2': 20}
```

## Tổng kết

Như vậy ta đã tìm hiểu xong 4 cấu trúc dữ liệu cực kì quan trọng trong Python, hy vọng các bạn có thể nắm vững và áp dụng đúng mục đích sử dụng. Ta có bảng tổng kết:

| List | Tuple | Set | Dict |
| :------ |:--- | :--- | :--- |
| Có thể chứa bất kì kiểu dữ liệu nào | Có thể chứa bất kì kiểu dữ liệu nào | Có thể chứa bất kì kiểu dữ liệu nào | Dữ liệu lưu dưới dạng key-value|
| Mutable(có thể sửa đổi các phần tử) | Immutable(không thể sửa đổi các phần tử) | Mutable(có thể sửa đổi các phần tử) | Mutable(có thể sửa đổi các phần tử) trong value của key|
| list_example = [1, 2, [3, 4]] | tuple_example = (1, 2, 2, 1) | set_example = {1, 2, 7, 8} | dict_example = {2: 'abc', 'item_2': 20}|


