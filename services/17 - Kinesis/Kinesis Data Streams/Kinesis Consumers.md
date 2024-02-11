A _consumer_ is an application that processes data from a Kinesis data stream.

Consumers can be:
- AWS Lambda functions
- Kinesis Data Analytics
- Kinesis Data Firehose
- Custom Consumer (AWS SDK) - Classic or Enhanced Fan-Out
- Kinesis Client Library (KCL)

# Custom Consumers

We have two options for custom consumers

### Shared (Classic) Fan-out Consumer
*Pull model*

![[Pasted image 20240210183322.png]]

Consumers will poll data from Kinesis using the **GetRecords** API call. All consumers combined can have the maximum throughput of **2 MB/s per shard**. 

We can call the GetRecords API a maximum 5 times/second and it has ~200 ms latency

The maximum size of data that GetRecords can return is 10 MB. If a call returns this amount of data, subsequent calls made within the next 5 seconds throw The maximum number of records that can be returned per call is 10,000.

This option is good when we have a low number of consuming applications and we want to lower costs.

### Enhanced Fan-out Consumer
*Push model*

![[Pasted image 20240210183332.png]]

Consumers will subscribe to shards with the SubscribeToShard API all and then Kinesis will push data to the subscribed consumers. We get a maximum throughput of **2 MB/s per consumer per shard**.

There is ~70 ms latency when receiving data and there is a soft limit of 5 consumer applications (KCL) per data stream (This can be raised by contacting AWS support).

This option is good when we have a higher number of consuming applications, but it is more expensive than the shared option.

# AWS Lambda as Kinesis consumer

AWS Lambda supports both classic and enhanced fanout consumers.

It will read records in batches and we can configure the batch size and batch window. If an error occurs, Lambda will retry until success or until the data expires.

We can process up to 10 batches per shard simultaneously.

![[Pasted image 20240210185345.png]]