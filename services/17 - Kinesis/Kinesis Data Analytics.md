
### Kinesis Data Analytics for SQL

With Amazon Kinesis Data Analytics for SQL Applications, you can process and analyze streaming data using standard SQL. The service enables you to quickly author and run powerful SQL code against streaming sources to perform time series analytics, feed real-time dashboards, and create real-time metrics.

It is a fully managed service, there are no servers to provision. It provides automatic scaling capability and you pay for the actual consumption rate

![[Pasted image 20240210204429.png]]

The source can only be a Kinesis Data Streams stream or a Kinesis Data Firehose stream. After we receive data, we can perform SQL statements on it and optionally enrich it with references to data in S3. We can send the query results to sinks, which can again be Kinesis Data Firehose or Kinesis Data Streams.

Use cases:
- Time-series analytics
- Real-time dashboards
- Real-time metrics

# Kinesis Data Analytics for Apache Flink
This has been renamed to Amazon Managed Service for Apache Flink, but it may come up in the exam with the old name

Managed Service for Apache Flink is a fully managed Amazon service that enables you to use an Apache Flink application to process streaming data.

An Apache Flink application is a Java or Scala application that is created with the Apache Flink framework. It is used for processing and analyzing data and it is much more powerful than SQL.

Features of this service:
- Automatically provisions resources
- Parallel computation
- Automatic scaling
- Application backups (implemented as checkpoints and snapshots)

Note that **Flink does not read from Firehose** (we have to use Kinesis Analytics for SQL instead)