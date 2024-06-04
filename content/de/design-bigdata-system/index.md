---
title: "Introduction and How to Design Big Data Systems"
date: 2024-05-04 13:48:00
draft: false
aliases:
    - /notes/design-bigdata-system.html
---

<div>
    <div style='display: inline-flex; list-style-type: none; padding-top: 15px;'>
        <li>
            <img src='https://visitor-badge.laobi.icu/badge?page_id=dnguyenngoc.github.io-de-design-bigdata-system&left_text=Visitors'/>
        </li>
    </div>
</div>

To kickstart the development of such a system, the first step is to design the data architecture depending on the project's requirements. For the project I'm involved in, the system needs to handle data from various sources in two main formats: real-time data processing and batch processing. A comprehensive diagram of the data pipeline is presented below to illustrate how the data is processed and accessed within the system. All code has been uploaded repo [github-big-data](https://github.com/dnguyenngoc/big-data)


<img src='img/DataArchitecture.png' style='white-space:nowrap;'/>


(<span style="color:red">In development, please wait everyone</span>)
Continue ...

<!-- Một hệ thống Bigdata thường bao gồm các layer chính là storage, computing và visualization. 
storage là nơi lưu trử toàn bộ dữ liệu của hệ thống trong th của tôi bao gồm s3(minio) và kafka.

Computing thì rất đa dạng component tuỳ thuộc vào nhu cầu sử dụng của mỗi tổ chức. Ví dụ airflow, airbyte, spark, cdc(debezium,kafka-connect), druid, ...

và cuối cùng là visualization layer bao gồm những công cụ để trực quan hoá data như superset, powerbi, ...

bên cạnh những layer chính một thành phần khác khá quan trọng là những công cụ hổ trợ analysis (analysis layer) dành cho developer, DA,DE,DS như jupyterlab, dbt là cần thiết.

ngoài ra tuỳ thuộc vào nhu cầu của mỗi hệ thống mà sẽ có thêm các thành phần đặc thù khác như high-query-engine(trino) hoặc streaming engine (druid, spark-streaming, ...) -->

