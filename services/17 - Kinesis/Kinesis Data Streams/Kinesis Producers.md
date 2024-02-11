An Amazon Kinesis Data Streams producer is an application that puts user data records into a Kinesis data stream (also called _data ingestion_).

These data records consist of:
- **Sequence number** - which is assigned by Kinesis Data Streams. It will be unique per partition key of the shard.
- **Partition key** - used to group data by shard within a stream. Kinesis Data Streams uses the partition key that is associated with each data record to determine which shard a given data record belongs to. A producer must specify a partition key when it wants to put data in a stream.
- **Data blob** - immutable sequence of bytes, can be up to 1MB

We can make our applications into producers with:
- **AWS SDK** - For creating very simple producers
- **Kinesis Producer Library** (KPL) - The KPL is built on top of the AWS SDK and it performs many tasks common to creating efficient and reliable producers for Kinesis. By using the KPL, customers do not need to develop the same logic every time they create a new application for data ingestion.
- **Kinesis Agent** - stand-alone Java software application that offers an easy way to collect and send data to Kinesis Data Streams.

For write throughput, we get 1MB/s or 1000 records/s per shard

We use the **PutRecord API** to put data into Kinesis streams

We can use batching with the PutRecord API to reduce costs & increase throughput (the KPL does this for us already)

### Example: Distributed partition key with Device Id

![[Pasted image 20240210135034.png]]

In this example, we have chosen the Device Id to be the partition key that we send to the stream. These partition keys will go through hash functions which will determine the shard they will go to.

We need to make sure our partition is well distributed to avoid a "hot partition" (IE a shard that takes most of the traffic).

For example, a user id in a system with hundreds of thousands of users would be a well distributed key. But, choosing the browser they use as a partition key would probably cause the shard where Chrome gets routed to take a majority of the traffic.

### ProvisionedThroughputExceeded

When we attempt to send more than 1MB/s or 1000 records/s to a shard we will get the ProvisionedThroughputExceeded exception.

Depending on the scenario, we have the following options to fix the issue:
- Use a highly provisioned partition key
- Implement retries with exponential backoff
- Increase the number of shards (scale)