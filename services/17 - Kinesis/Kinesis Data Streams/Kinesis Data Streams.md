Kinesis data streams is a serverless service that makes it easy to capture, process, and store data streams

### Key concepts

A _Kinesis data stream_ is a set of shards.

A **_shard_** is a unit of capacity that provides 1 MB/second of write and 2 MB/second of read throughout. You're charged for each shard at an hourly rate.

 Each shard has a sequence of data records. 

A **_data record_** is the unit of data stored in a Kinesis data stream. Data records are composed of a sequence number, a partition key, and a data blob, which is an immutable sequence of bytes.

**_Producers_** put records into Amazon Kinesis Data Streams. For example, a web server sending log data to a stream is a producer.

**_Consumers_** get records from Amazon Kinesis Data Streams and process them.

![[Pasted image 20240208231715.png]]

### Key properties

Retention can be set from 1 day to 365 days and by default you have the ability to reprocess (replay) data

Once data is inserted in Kinesis, it can't be deleted (it is immutable)

When you send data to data streams, you set a partition key. Messages that share the same partition key will go to the same shard which gives us per-key based ordering.

Producers you can use:
- AWS SDK
- Kinesis Producer Library (KPL)
- Kinesis Agent

For consumers:
- Write your own with:
	- Kinesis Client Library (KCL)
	- AWS SDK
- Managed consumer on AWS
	- AWS Lambda
	- Kinesis Data Firehose
	- Kinesis Data Analytics

### Capacity Modes

You have two options for capacity modes

**Provisioned Mode**:
- You choose the number of shards provisioned, scale manually or using API
- Each shard gets 1MB/s in (or 1000 records per second)
- Each shard gets 2MB/s out
- You pay per shard per provision per hour

**On-Demand Mode**:
- No need to provision or manage the capacity
- Default capacity provisioned (4MB/s in or 4000 records/s)
- Scales automatically based on observed throughput peak during the last 30 days
- Pay per stream per hour & data in/out per GB

# Security

We can control access and authorization using IAM policies

For encryption we have the following options:
- Encryption in flight using HTTPS
- Encryption at rest using KMS
- Client side encryption/decryption

VPC Endpoints are available to Kinesis to access with VPC

We can also monitor the API calls using CloudTrail