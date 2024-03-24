---
layout: post 
title: <b>Mình dùng tool gì để vẽ các Diagram, đồ thị?</b>
subtitle: Obsidian and Excalidraw plugin
tags: [Sharing]
cover-img: /assets/img/sharing/img_1.png
comments: true
---

Chào các bạn, khi làm việc chúng ta sẽ có những công việc cần lưu ý, những kiến thức hay cần ghi nhớ, những đoạn code hay cần được note lại.
Thông thường thì các bạn sẽ sử dụng tool gì để viết note nhỉ? Mình khá chắc là hiện tại có rất là nhiều note tool chẳng hạn như:
- Notion: cái này có bản Personal và cho Team. Notion cho phép người dùng tạo ra các website, các bạn báo cáo nhanh, các công cụ cũng rất đa dạng như **table, list, hay tích hợp tools của bên thứ 3 vào**
- Microsoft Notes: cái này mình thấy một số anh chị xài chung với hệ sinh thái của Microsoft, nó cũng rất mạnh (nhưng mà mình không thích là nó không cho hightlight code :D)
- Obsidian: tool note mà mình sẽ giới thiệu trong bài này. Nó sử dụng _markdown_ language để hiển thị, điểm mạnh của Obsidian là cho phép người  dùng cài thêm các bộ plugin và có khá nhiều phím tắt. Mình hay note và thường vẽ các đồ thị, diagram để đính kém vào trong note luôn, nên Obsidian và Excalidraw(plugin để vẽ vời :D) là một giải pháp tuyệt vời.

Bắt tay vô xem Obsidian và Excalidraw là cái gì nào !!
![OOP trong python](/assets/img/5.python-oop/4-oop.png)

## 1. Obsidian là gì? Cài đặt và hướng dẫn tạo một cái note đơn giản.
### Cài đặt Obsidian
Obsidian là phần mềm free, các bạn có thể tải tại [trang chủ](https://obsidian.md/) của nó.\
![Obsidian](/assets/img/sharing/img_2.png) 

Sau khi cài xong các bạn cài đặt như bình thuờng. Giao diện của Obsidian sẽ như sau:
![Giao diện](/assets/img/sharing/img_3.png) 

### Tạo một cái note đơn giản.
**Obsidian** hỗ trợ rất nhiều phím tắt (shortcut) giúp tăng tốc độ làm việc. Các bạn có thể tìm một số shortcut hữu ích và hay sử dụng [tại đây](https://forum.obsidian.md/t/obsidian-hotkeys-favorites-and-best-practices/12125)

Để tạo mới một note, các bạn chọn _Create new file_ hoặc **Ctrl + N** (macos Cmd + N)

### Cách sử dụng

1. **Mở đầu**
2. 

![Class và Object](/assets/img/5.python-oop/class-object.png)

Triển code luôn cho dễ hiểu, code flow sẽ như sau:
1. Tạo 1 class Person với thuộc tính là chiều cao và ngôn ngữ bằng hàm **__init__**
2. Tạo một phương thức **say_hello**, tuỳ vào Person ở nước nào mà sẽ có phương thức say_hello khác nhau

```python
# Khai báo class
class Person:
    def __init__(self, height: float, language: str):
        pass

    def say_hello(self):
        return f"I'm come from {language}"

# Khởi tạo object từ class
john = Person(height=190.5, language="English")
john.say_hello()

nick = Person(height=180, language="Vietnam") 
nick.say_hello()

```

## 2. OOP trong Python
Trong phần này, chúng ta sẽ lấy lại ví dụ về lớp **Person**.

### Tính kế thừa (Inheritance)
> **Usecase**: Tính kế thừa giúp việc tạo các Class mới từ các Class đã tồn tại với việc thêm vào hoặc sửa chữa các thuộc tính, phương thức của Class cũ. Điều này giúp giảm tình trạng reuse code, khi bạn sử dụng kế thừa, class mới sẽ tự động sử dụng lại tất cả các code cũ mà không cần phải copy thứ gì từ nó.

Giả sử lớp mọi con người đều nói được _Hello world !!!_, thì ta chỉ cần khai báo phương phức **speak** trong Person để các lớp khác có thể sử dụng.

```python
class Person():
    def speak():
        print("Hello world!!!")
        return
        
class PersonAsia(Person):
    pass

person = PersonAsia()
person.speak()
# output: Hello world!!!

```
Bằng cách sử dụng tính kế thừa mà lớp _PersonAsia_ không cần phải khai báo lại phương thức _speak_ mà có thể sử dụng nó từ lớp cha Person


### Tính trừu tượng (Abstraction)
> **Usecase**: Khi một Class con được khởi tạo, nó sẽ kế thừa mọi thuộc tính và phương thức từ lớp cha của nó. Làm sao để lớp con có thể thay thế hay ghi đè lớp cha? Đó chính là đặc trưng của tính trừu tượng. Tính trừu tượng cho phép các lớp con ghi đè lại các phương thức hay thuộc tính của lớp cha.



### Tính đa hình (Polymorphism)
> **Usecase**: hai hay nhiều lớp có phương thức giống nhau nhưng lại thực hiện các hành vi theo những các thức khác nhau

Ví dụ:
```python
class PersonX():
    def speak()):
        print("Im X person")

class PersonY():
    def speak():
        print("Im Y person")

def person_speak(person):
    person.speak()


person_x = PersonX()
person_speak(person_x)
# Im X person

person_y = PersonY()
person_speak(person_y)
# Im Y person

```

### Tính đóng gói (Encapsulation)
> **Usecase**: đây là một trong những tính chất quan trọng của Lập trình hướng đối tượng. Tính đóng gói giúp ngăn chặn việc truy cập, thay đổi thuộc tính, phương thức của một lớp một cách trực tiếp, giúp che giấu dữ liệu (data hiding)

Về cơ bản, trong Python không có các thuộc tính, phương thức **private, public hay protected** như Java hay C#, nó được thực hiện theo cách khác

Các thuộc tính hay phương thức _private_ chỉ có thể được sử dụng bên trong lớp chứa nó, Python sử dụng hai dấu gạch dưới (prefix) để làm tiền tố chỉ định một thuộc tính hay phương thức private.

## 3. Tổng kết
Qua bài viết vừa rồi, mình và các bạn đã đi qua các khái niệm cơ bản cũng như tính chất quan trọng trong lập trình hướng đối tượng.

Python là ngôn ngữ hỗ trợ lập trình hướng đối tượng, tuy nhiên việc thể hiện tính chất **hướng đối tượng** của Python thật sự không rõ ràng như Java hay C#.

Tuy nhiên OOP trong Python vẫn là một đặc trung rất hay, rất hữu ích trong quá trình phát triển phần mềm. Ở các bài tiếp theo mình sẽ đi sâu hơn và cụ thể hơn về OOP trong Python.
Hẹn gặp các bạn ở bài sau !

* TOC
{:toc}