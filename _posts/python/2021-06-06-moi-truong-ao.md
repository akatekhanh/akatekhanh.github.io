---
layout: post 
title: 2. Cài đặt môi trường ảo cho python
subtitle: Môi trường ảo là gì? Tại sao chúng ta nên sử dụng môi trường ảo?
tags: [Python cơ bản]
comments: true
---

Python là một ngôn ngữ hiện đại, có hàng ngàn các thư viện và module khác nhau hỗ trợ người dùng, đây là một lợi ích rất lớn của Python. Và cũng chính vì có quá nhiều các gói thư viện(module) như vậy nên cũng có một vài vấn đề xảy ra với nó.

Giả sử ta có hai Project là **Project A** và **Project B**, hai Project này đều chạy chung 1 thư viện là **requests**, tuy nhiên **Project A** xài requests module version 1.0.0, **Project B** xài requests module 2.0.0. Điều này sẽ dẫn đến một số sự xung đột về phiên bản (conflict), vấn đề đặt ra làm sao mà ta có thể tách biệt thư viện của hai Project này ra sao cho chúng không con xung đột nữa.

Thật may, hoàn toàn có một công cụ giúp ta làm được điều đó, đó là tách biệt môi trường cho những _Python project_ khác nhau. Đó là **_Python virtual environment_**. Công cụ này giúp ta tạo các môi trường ảo khác nhau, không giới hạn số lượng chỉ với một vài câu lệnh.

## Sử dụng Môi trường ảo (Virtual Environment)

Để bắt đầu, yêu câu là phải có python version 3. Để kiểm tra version của python hiện ta ta sử dụng.
```bash
python3 --version
```

**Cài đặt virtualenv tool cho Linux**
```bash 
sudo apt install python3-virtualenv
```
![Môi trường ảo](/assets/img/moi-truong-ao/virtualenv.jpeg)
**Tạo môi trường ảo**
```bash
virtualenv test_env
```
Với **test_env** là tên của môi trường ảo.

**Kích hoạt môi trường ảo**
```bash
source test_env/bin/activate
```
Lưu ý là ta phải đang đứng ở thư mục chứa thư mục của môi trường ảo nhé.

**Cài đặt các package cho Project**
```bash 
pip install <Tên package cần cài>

# Ví dụ: pip install requests
```

**Deactivate một môi trường ảo đang chạy**
```bash
deactivate
```





