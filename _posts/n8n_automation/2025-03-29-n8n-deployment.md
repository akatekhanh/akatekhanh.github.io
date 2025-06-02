---
layout: post
# permalink: /n8n/:title/
categories: n8n
title: (Seft host) Deploy N8N Automation trên Docker Compose với Traefik và PostgreSQL
subtitle: Triển khai Automation Workflow n8n kèm SSL tự động trên Vultr VPS
share-img: /assets/img/n8n_automation/workflow.png
tags: [DevOps, Docker, n8n, Vultr]
comments: true
---
![](/assets/img/n8n_automation/workflow.png)
## 🎯 Giới thiệu

Trong bài viết này, bạn sẽ được hướng dẫn cách triển khai **n8n - nền tảng Automation Workflow** trên **Vultr VPS** sử dụng **Docker Compose**, kết hợp với:

- **Traefik Reverse Proxy** (kèm SSL Let's Encrypt)
- **PostgreSQL (pgvector)**
- Dynamic Routing & HTTPS tự động

---

## 🟢 Yêu cầu chuẩn bị

- VPS (Ubuntu 22.04 LTS hoặc tương tự)
- Tên miền và subdomain. Ví dụ:
  - DOMAIN_NAME: `example.com`
  - SUBDOMAIN: `automation`
- Email để đăng ký SSL Let's Encrypt
- SSH access vào VPS
---

## 🌐 Tạo bản ghi A record trên Namecheap

Để tên miền của bạn trỏ đúng về server VPS, cần tạo A record như sau:

### Các bước:

1. Truy cập [https://namecheap.com](https://namecheap.com) và đăng nhập.
2. Vào mục **Domain List** → nhấn nút **Manage** tại domain của bạn.
3. Chuyển đến tab **Advanced DNS**
4. Tại mục **Host Records**, nhấn **Add New Record** và thêm:

| Type | Host       | Value (IP VPS)    | TTL       |
| ---- | ---------- | ----------------- | --------- |
| A    | automation | `123.123.123.123` | Automatic |

> 📝 Ghi chú:
> - `automation` là subdomain bạn dùng cho n8n.
> - `123.123.123.123` là IP của VPS của bạn.
> - Nếu bạn muốn dùng root domain (`@`), bạn có thể thêm thêm 1 A record nữa.

Chờ khoảng 1-10 phút để DNS được cập nhật.
---

## ⚙️ Cài đặt môi trường

### 1. Cài Docker & Docker Compose

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose
sudo systemctl enable docker
sudo systemctl start docker
```

### 2. Tạo Docker Volumes
docker volume create traefik_data
docker volume create n8n_data
docker volume create pgdata

### 3. Tạo file .env
Tạo file .env tại thư mục chứa docker-compose.yml:
DOMAIN_NAME=example.com
SUBDOMAIN=automation
SSL_EMAIL=your_email@example.com
GENERIC_TIMEZONE=Asia/Ho_Chi_Minh


