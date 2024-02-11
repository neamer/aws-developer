Kinesis Data Streams can have similar use cases to SQS FIFO queues. We will compare these two through a example to see the differences.

Example: We have 100 trucks on the road sending GPS positions regularly into AWS. We want to consume the data in order for each truck, so that we can track their movements accurately

### Ordering data into Kinesis

We will send the data into Kinesis with a partition key with the value of the truck Id.

With this setup, the same key will always go to the same shard.

![[Pasted image 20240210210300.png]]

### Ordering data into SQS FIFO

If we don't use a Group ID, the messages will only be able to have one consumer.

![[Pasted image 20240210210421.png]]

To scale the number of consumers, we can use a Group ID

![[Pasted image 20240210210508.png]]

# Conclusion

Lets assume that we provisioned 5 shards for the 100 trucks, vs 1 SQS FIFO queue for the 100 trucks

Kinesis Data Streams:
- On average you will have 20 trucks per shard
- The maximum amount of consumers in parallel we can have is 5
- Can receive up to 5 MB/s of data

SQS FIFO:
- We can use the vehicle id as a Group ID to maximize groups while keeping the data consumption chronological.
- This means that we can have up to 100 consumers
- Up to 300 messages/s (or 3000 if we use batching)

We can see that Kinesis Data Streams will be better if we need higher throughput, while SQS FIFO will be better if we need to maximize the number of consumers.