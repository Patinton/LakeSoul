[CN Doc](README-CN.md)

# LakeSoul
LakeSoul is a unified streaming and batch table storage for fast data processing built on top of the Apache Spark engine by the [DMetaSoul](https://www.dmetasoul.com) team, and supports scalable metadata management, ACID transactions, efficient and flexible upsert operation, schema evolution, and streaming & batch unification.

LakeSoul implements incremental upserts for both row and column and allows concurrent updates on the same partition. LakeSoul uses LSM-Tree like structure to support updates on hash partitioning table with primary key, and achieve very high write throughput (30MB/s/core) on cloud object store like S3 while providing optimized merge on read performance. LakeSoul scales meta data management by using distributed NoSQL DB Cassandra.

More detailed features please refer to our wiki page: [Wiki Home](https://github.com/meta-soul/LakeSoul/wiki/Home)

Some features and performance comparisons: [Data Lake Comparison](https://github.com/meta-soul/LakeSoul/wiki/01.-Data-Lake-Comparison)

# Usage Documentations
Please find usage documentations in project's wiki:
[Usage Doc](https://github.com/meta-soul/LakeSoul/wiki/03.-Usage-Doc)

[使用文档](https://github.com/meta-soul/LakeSoul/wiki/%E4%BD%BF%E7%94%A8%E6%96%87%E6%A1%A3)

Follow the [Quick Start](https://github.com/meta-soul/LakeSoul/wiki/02.-QuickStart) to quickly setup a test env.

Checkout the [CDC Ingestion with Debezium and Kafka](https://github.com/meta-soul/LakeSoul/tree/main/examples/cdc_ingestion_debezium) example on how to sync LakeSoul table with OLTP dbs like MySQL in a realtime manner.

# Feature Roadmap
* Meta Management
  - [x] Multiple Level Partitioning: Multiple range partition and at most one hash partition
  - [x] Concurrent write with optimistic lock mechanism
  - [x] MVCC with read isolation
  - [x] Write atomicity through Cassandra's Light Weight Transaction
* Table operations 
  - [x] LSM-Tree style upsert for hash partitioned table
  - [x] Merge on read for hash partition with upsert delta file
  - [x] Copy on write update for non hash partitioned table
  - [x] Compaction
* Spark Integration
  - [x] Table/Dataframe API
  - [x] SQL support with catalog except upsert
  - [x] Query optimization
    - [x] Shuffle/Join elimination for operations on primary key
  - [x] Merge UDF (Merge operator)
  - [ ] Merge Into SQL support
    - [x] Merge Into SQL with Primary Key
    - [ ] Merge Into SQL with non-pk
* Flink Integration
  - [ ] Table API
  - [ ] Flink CDC
* Realtime Data Warehousing
  - [ ] CDC ingestion and time travel
  - [ ] Event driven materialized view build and compaction
* Cloud Native
  - [ ] Object storage IO optimization
  - [ ] Multi-layer storage classes support with data tiering

# Feedback and Contribution
Please feel free to open an issue if you have any questions.

# Contact Us
[opensource@dmetasoul.com](mailto:opensource@dmetasoul.com)

# Opensource License
LakeSoul is opensourced under Apache License v2.0.
