---
layout: post
categories: data-engineer
permalink: /:categories/:title/
title: Apache Iceberg là gì? Khái niệm chính - Kiến trúc - Thực hành
subtitle: Tìm hiểu về Apache Iceberg - Table format cho Big Data
# cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/data_engineer/tabular_format/2025-05-04-apache-iceberg/thumbnail.png
share-img: /assets/img/path.jpg
tags: [Data engineer, Tabular format]
comments: true
---
Khi làm việc và xử lý với dữ liệu lớn, các giai đoạn Load, Transform và Extract data có khả năng gây ra lỗi, các lỗi mà quá trình ETL ta thường
gặp phải bao gồm như ghi đè dữ liệu, xoá dữ liệu, hoặc làm hỏng các bảng dữ liệu.

Apache Iceberg ra đời để giải quyết các thách thức mà ta đã đề cập ở trên. Bằng việc cung cấp một lớp quản lý, quản trị phía bên trên các 
File dữ liệu (như Parquet, ORC), từ đó hỗ trợ và đảm bảo việc khôi phục, xử lý các vấn đề về dữ liệu nhanh chóng, đồng thời giúp tối ưu hoá các 
chiến lược lựa chọn và Load các File dữ liệu lên các công cụ tính toán (compute engine) như Apache Spark, Apache Flink,...

Ở bài viết này, chúng ta sẽ cùng đi tìm hiểu về Apache Iceberg, các khái niệm cơ bản, cách thức hoạt động và kiến trúc của nó. Chúng ta sẽ 
cùng thực hành từng bước, sử dụng Docker với Pyspark và Iceberg.
* TOC
{:toc}


# 1. Giới thiệu
Các kiến trúc Data Lake, Data Lakehouse hiện tại yêu cầu về độ tin cậy, khả năng mở rộng và hiệu suất trên các nền tảng Data platform. Apache 
Iceberg là một dạng **table format** hỗ trợ cho các tác vụ Big Data Analytic, trên quy mô lớn, đảm bảo độ tin cậy, chính xác. Nó được Netflix 
phát triển nhằm khắc phục các điểm yếu của Apache Hive. Thay vì truy xuất (query) trực tiếp File dữ liệu qua Hive Metastore, Iceberg sử dụng thêm 
một lớp metadata phía trên các File dữ liệu (parquet hoặc ORC) và giao thức **transaction**, từ đó đạt được một số tính chất và đặc điểm của 
Datawarehouse bao gồm _ACID transaction (Atomicity-Consistency-Isolation-Durability)_, _Schema evolution_, _Time travel_ trong khi vẫn lưu trữ File dữ
liệu dưới các Object Storage trên Cloud với chi phí rẻ, và khả năng bền bỉ cao. Hơn nữa, Iceberg biến Data Lake thành Data Lakehouse, kết hợp 
được tính linh hoạt của Data Lake và khả năng tin cậy của SQL Database.

Iceberg giải quyết các khó khăn và bất lợi của các hệ thống File cũ như Hive bao gồm Schema evolution, và truy xuất File đồng thời (concurrent control):

## a. ACID transaction

## b. Schema evolutiev

# 2. Kiến trúc của Apache Iceberg và chức năng chính (function)



