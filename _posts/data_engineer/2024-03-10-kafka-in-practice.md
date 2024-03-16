---
layout: post
title: Kafka từ cơ bản tới nâng cao - Setup môi trường và thao tác cơ bản (part 2 - practice)
subtitle:  Kafka in practice
# cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/data_engineer/kafka_in_practice/architecture.png
share-img: /assets/img/path.jpg
tags: [Data engineer]
comments: true
---

Trong phần này, chúng ta sẽ đi qua quá trình setup môi trường và thực hiện một số thao tác cơ bản với Kafka bằng cách sử dụng Docker và Docker compose - phần setup khá đơn giản chỉ cần các bạn cài đặt Docker Desktop. Để bắt đầu, bạn cần cài đặt Kafka và Zookeeper trên máy của mình. Kafka sử dụng Zookeeper để quản lý và điều phối cluster, vì vậy việc cài đặt Zookeeper là bắt buộc.

* TOC
{:toc}

# Kafka từ cơ bản tới nâng cao - Setup môi trường và thao tác cơ bản

## Cài đặt và cấu hình Kafka
Để thiết lập môi trường Kafka sử dụng Docker, bạn cần thực hiện các bước sau:

1. Đầu tiên, bạn cần có Docker và Docker Compose được cài đặt trên máy của mình. Bạn có thể tải về và cài đặt từ trang chính thức của Docker.

2. Tiếp theo, clone repository chứa mã nguồn cấu hình Docker Compose cho Kafka và Zookeeper. Sử dụng lệnh sau để clone repository từ GitHub:
```bash
git clone https://github.com/akatekhanh/geeksdata.git
```

```bash
# Run docker compose to start Kafka container and Pyspark Notebook container
# -d means detach: run container in silence
docker compose up -d
```

Các bạn có thể mở file docker để tìm hiểu các Service bên trong đó:
```bash
version: '3.1'
services:
  spark:
    build: .
    volumes:
      - .:/home/jovyan/work
    ports:
      - "8888:8888"
    
  kafka:
    image: wurstmeister/kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_LISTENERS: INTERNAL://0.0.0.0:9092,OUTSIDE://0.0.0.0:9094
      KAFKA_ADVERTISED_LISTENERS: INTERNAL://kafka:9092,OUTSIDE://localhost:9094
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: INTERNAL:PLAINTEXT,OUTSIDE:PLAINTEXT
      KAFKA_INTER_BROKER_LISTENER_NAME: INTERNAL


    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    depends_on:
      - zookeeper

  kafka-ui:
    image: provectuslabs/kafka-ui
    ports:
      - "8080:8080"
    environment:
      KAFKA_CLUSTERS_0_NAME: local
      KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: kafka:9092
      DYNAMIC_CONFIG_ENABLED: 'true'
    depends_on:
      - kafka
  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    ports:
      - "2181:2181"
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000
```

File docker compose bao gồm các dịch vụ sau:

1. **Spark**: Dịch vụ này xây dựng một container từ Dockerfile trong thư mục hiện tại. Nó chia sẻ thư mục hiện tại của máy host với thư mục `/home/jovyan/work` trong container và mở cổng `8888` để truy cập Jupyter Notebook.

2. **Kafka**: Sử dụng image `wurstmeister/kafka` và cấu hình các biến môi trường như `KAFKA_BROKER_ID` và `KAFKA_ZOOKEEPER_CONNECT` để kết nối với Zookeeper. Cổng `9092` được mở cho Kafka và cấu hình listeners để cho phép kết nối từ bên trong và bên ngoài container.

3. **Kafka-UI**: Dịch vụ này sử dụng image `provectuslabs/kafka-ui` để cung cấp một giao diện người dùng qua web cho việc quản lý và giám sát Kafka cluster. Nó kết nối với Kafka thông qua cổng `9092` và mở cổng `8080` để truy cập từ trình duyệt.

4. **Zookeeper**: Sử dụng image `confluentinc/cp-zookeeper` và cấu hình các biến môi trường như `ZOOKEEPER_CLIENT_PORT` và `ZOOKEEPER_TICK_TIME`. Cổng `2181` được mở cho Zookeeper để kết nối với Kafka.

Cấu hình này giúp thiết lập một môi trường đơn giản để bắt đầu làm việc với Kafka, bao gồm việc produce và consume message, quản lý topic, và giám sát cluster thông qua Kafka UI. Đồng thời, việc tích hợp Spark giúp các bạn có thể kết nối tới Kafka và sủ dụng ngôn ngữ Python.

Các bạn có thể kiếm tra các service đang được chạy trên Docker và xem Kafka UI để có thể trực quan hoá Kafka message của mình.  

![Alt text](/assets/img/data_engineer/kafka_in_practice/image.png)

Truy cập vào `localhost:8080` để xem Kafka UI
![Alt text](/assets/img/data_engineer/kafka_in_practice/image-1.png)



## 3. Thao tác cơ bản với Kafka
- Tạo và quản lý Topic.
- Sản xuất (Produce) và tiêu thụ (Consume) message.

## 4. Kafka Producer và Consumer API
- Giới thiệu về Kafka Producer API.
- Giới thiệu về Kafka Consumer API.
- Ví dụ cơ bản về cách sử dụng Producer và Consumer API.

## 5. Quản lý và giám sát Kafka
- Công cụ quản lý và giám sát Kafka.
- Cách sử dụng các công cụ này để theo dõi và quản lý cluster Kafka.

## Kết luận
- Tổng kết những kiến thức đã học và áp dụng trong bài viết.
- Đề xuất hướng đi tiếp theo để tìm hiểu sâu hơn về Kafka.

Mục tiêu của bài viết này là cung cấp cho bạn cái nhìn tổng quan về cách thiết lập và sử dụng Kafka trong môi trường phát triển. Hy vọng rằng, sau khi đọc xong bài viết, bạn sẽ có đủ kiến thức cơ bản để bắt đầu làm việc với Kafka.

 