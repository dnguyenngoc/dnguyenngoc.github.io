---
title: "Apache Iceberg: The Open Table Format Reshaping the Data Lakehouse"
date: 2026-08-12
draft: false
description: "A practical, plain-English introduction to Apache Iceberg, the open table format that brings database-like reliability to cheap object storage and lets every engine share one copy of your data."
tags: ["apache iceberg", "data lakehouse", "data engineering", "open table format"]
featured_image: "https://images.viblo.asia/80181253-1bb4-4f9a-8767-bb8cac951f94.png"
aliases:
    - /notes/apache-iceberg-open-table-format-lakehouse.html
---
<div><div style='display: inline-flex; list-style-type: none; padding-top: 15px;'><li><img src='https://visitor-badge.laobi.icu/badge?page_id=dnguyenngoc.github.io-posts-apache-iceberg-open-table-format-lakehouse&left_text=Visitors'/></li></div></div>

For most of the last decade, companies faced an awkward choice. You could put your data in a **data warehouse** — fast and reliable, but expensive and locked into one vendor. Or you could dump it into a **data lake** — cheap cloud storage full of files, but slow, messy, and easy to corrupt. Apache Iceberg is the technology that finally lets you stop choosing. It has quietly become one of the most important developments in modern data engineering, and in 2025 and 2026 nearly every major data platform — Snowflake, Databricks, Google BigQuery, and AWS — announced deep support for it.

This post explains what Iceberg is, why it matters, and how to start using it, in language that does not assume you are a data engineer.

## The problem Iceberg solves

Imagine your company stores millions of sales records as files in cloud storage such as Amazon S3. This is attractive because object storage is extremely cheap and can hold unlimited data. The trouble starts when people want to actually *use* that data.

- If someone is reading the files while another process is writing new ones, the reader can see a half-finished, broken picture.
- Renaming a column or fixing a data type often means rewriting everything from scratch.
- Nobody can easily answer a simple question like "what did this table look like last Tuesday?"
- Every analytics tool needs its own copy or its own understanding of where the files are.

A traditional database solves these problems with a hidden layer of bookkeeping. Apache Iceberg brings that same bookkeeping to plain files sitting in cheap storage. It is best described as an **open table format**: a specification and a set of metadata files that turn a folder of raw data files into a proper, well-behaved table.

Crucially, Iceberg is *open*. It was created at Netflix, donated to the Apache Software Foundation, and is not owned by any single vendor. That openness is exactly why so many competing platforms have agreed to support it.

## What you actually get

Iceberg gives your data lake the features people expect from a real database:

- **ACID transactions.** Writes either complete fully or not at all, so readers never see corrupt, half-written data. Multiple jobs can write safely at the same time.
- **Time travel.** Every change creates a new snapshot, so you can query the table exactly as it looked at any point in the past — invaluable for audits, debugging, and reproducing yesterday's report.
- **Safe schema evolution.** You can add, rename, drop, or reorder columns without rewriting the underlying data or breaking existing queries.
- **Hidden partitioning.** Iceberg manages how data is organised for speed behind the scenes, so analysts do not need to memorise partitioning rules to write fast queries.
- **Engine independence.** The same Iceberg table can be read and written by Spark, Trino, Flink, Snowflake, DuckDB, and many others — one copy of the data, many tools.

That last point is the heart of the current excitement. Instead of copying data into each system, teams keep a single authoritative copy and point every engine at it.

## How it works, briefly

Under the hood, an Iceberg table is a layered set of metadata files that sit alongside your data files (usually in the efficient Parquet format).

At the top is a small **catalog** entry that always points to the current version of the table. Below that, **metadata files** describe the table's schema and history. **Manifest files** then list exactly which data files belong to each snapshot. Because a write only needs to create new metadata pointing to new files, publishing a change is a single, atomic swap — that is what makes concurrent access safe.

The catalog has become a hot area of its own. The **Iceberg REST Catalog** is a standard way for any tool to discover and talk to Iceberg tables over a simple web API, which is why open catalogs such as Apache Polaris and Unity Catalog are now common talking points.

## A quick hands-on example

You can experiment with Iceberg on your laptop using PySpark. The snippet below configures a local Iceberg catalog, creates a table, writes some rows, and then queries an older snapshot.

```python
from pyspark.sql import SparkSession

# Configure Spark with the Iceberg extension and a local catalog
spark = (
    SparkSession.builder
    .appName("iceberg-demo")
    .config("spark.sql.extensions",
            "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions")
    .config("spark.sql.catalog.local", "org.apache.iceberg.spark.SparkCatalog")
    .config("spark.sql.catalog.local.type", "hadoop")
    .config("spark.sql.catalog.local.warehouse", "/tmp/iceberg_warehouse")
    .config("spark.jars.packages",
            "org.apache.iceberg:iceberg-spark-runtime-3.5_2.12:1.7.1")
    .getOrCreate()
)

# Create a table and insert some rows
spark.sql("""
    CREATE TABLE local.db.sales (id BIGINT, product STRING, amount DOUBLE)
    USING iceberg
""")
spark.sql("INSERT INTO local.db.sales VALUES (1, 'keyboard', 49.9), (2, 'mouse', 19.5)")

# Schema evolution: add a column without rewriting data
spark.sql("ALTER TABLE local.db.sales ADD COLUMN region STRING")

# Inspect the snapshot history
spark.sql("SELECT * FROM local.db.sales.snapshots").show()
```

To read the table as it looked at an earlier point in time, you simply reference a snapshot:

```python
# Time travel: read an earlier version of the table
spark.sql("""
    SELECT * FROM local.db.sales
    VERSION AS OF <snapshot_id_from_above>
""").show()
```

Prefer something lighter? The `pyiceberg` library lets you read and write Iceberg tables in pure Python without Spark, which is handy for smaller pipelines and for loading data straight into pandas.

```shell
pip install "pyiceberg[pyarrow]"
```

## Iceberg, Delta Lake, and Hudi

Iceberg is not the only open table format. **Delta Lake**, created at Databricks, and **Apache Hudi**, born at Uber, aim at the same goals. All three offer ACID transactions, schema evolution, and time travel. The practical differences come down to ecosystem: Delta Lake is deeply tied to the Spark and Databricks world, Hudi shines for streaming and change-data-capture workloads, and Iceberg has won broad, vendor-neutral adoption as the common standard.

Encouragingly, the industry is converging rather than fragmenting. Tools like Delta Lake UniForm now let a single dataset be read as either Delta or Iceberg, reducing the risk of picking the "wrong" format. For teams that value flexibility and want to avoid lock-in, Iceberg is increasingly the safe default.

## Should your team care?

If your organisation stores large volumes of analytical data in cloud object storage and struggles with reliability, duplicated copies, or vendor lock-in, Iceberg is worth a serious look. It lets you keep the low cost of a data lake while gaining the trustworthiness of a warehouse, and it keeps your options open as tools and vendors change around you.

The best way to start is small: pick one dataset, load it into an Iceberg table, and let two different engines query it. Once your team experiences one copy of data serving many tools — safely and with a full history — the appeal becomes obvious.

## References

- [Apache Iceberg official documentation](https://iceberg.apache.org/docs/latest/)
- [PyIceberg documentation](https://py.iceberg.apache.org/)
- [The Evolution of Apache Iceberg Catalogs — Dremio](https://www.dremio.com/blog/the-evolution-of-apache-iceberg-catalogs/)
- [Lakehouse format convergence: Delta Lake & Iceberg — Capital One Tech](https://www.capitalone.com/tech/cloud/lakehouse-format-convergence-delta-lake-iceberg/)
- [Apache Iceberg vs. Delta Lake vs. Hudi — e6data](https://www.e6data.com/blog/apache-iceberg-vs-delta-lake-vs-hudi)
- [Apache Iceberg features and benefits — OLake](https://olake.io/blog/apache-iceberg-features-benefits/)
