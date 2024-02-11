
The _Fanout_ scenario is when a message published to an SNS topic is replicated and pushed to multiple endpoints, such as Kinesis Data Firehose delivery streams, Amazon SQS queues, HTTP(S) endpoints, and Lambda functions. This allows for parallel asynchronous processing.

### SNS and SQS to decouple application event publishing

![[Pasted image 20240208221605.png]]

The main advantages for this approach over direct connection between the services:
- Fully decoupled model
- SQS allows for data persistence, delayed processing and retries of work if needed
- Ability to easily add more endpoints over time
- Cross-Region Delivery, or the ability to work with SQS queues in different regions

For this to work we need to make sure that the endpoints access policy allows for SNS to write.

### S3 Events to multiple queues

We have [[S3 Event Notifications]] for sending events about S3 activities. However, a limitation exists where you can only have one Event rule per event type (e.g. ObjectCreate) and prefix (e.g. img/).

Thus, we can use the fanout pattern to send an S3 Event to many endpoints

![[Pasted image 20240208223916.png]]

### SNS to Amazon S3 through Kinesis Data Firehose

SNS has direct integration with Kinesis Data Firehose, therefore we can have the following architecture for sending SNS events to S3 (or any other KDF destination)

![[Pasted image 20240208224129.png]]

### FIFO Topics

Amazon SNS has the option to order messages in topic in a FIFO manner.

![[Pasted image 20240208225745.png]]

We have many similar features to SQS FIFO Queues:
- Ordering by Message Group ID (all messages in the same group are ordered)
- Deduplication using deduplication id or content based deduplication
- Same limited throughput

The subscribers can be Standard SQS Queues and FIFO SQS Queues

If we needed ordering and deduplication for the decoupling example from above, we could simply have the topic be a FIFO Topic and SQS queues be FIFO

![[Pasted image 20240208225950.png]]

