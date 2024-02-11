_FIFO (First-In-First-Out)_ queues have all the capabilities of the [standard queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/standard-queues.html), but are designed to enhance messaging between applications when the order of operations and events is critical, or where duplicates can't be tolerated.

We have exactly-once send capability and exact message ordering, but there is a draw back in the throughput. It is limited to 300 msg/s without batching and 3000 msg/s with

![[Pasted image 20240206222020.png]]

# Advanced Concepts

### Deduplication

Unlike standard queues, FIFO queues don't introduce duplicate messages. FIFO queues help you avoid sending duplicates to a queue. If you retry the `SendMessage` action within the 5-minute deduplication interval, Amazon SQS doesn't introduce any duplicates into the queue.

There are two methods for deduplication:
- Content-based deduplication: A SHA-256 hash of the message body is created and used to compare messages.
- Message Deduplication ID: A Id that we send with each message. If a message with a particular message deduplication ID is sent successfully, any messages sent with the same message deduplication ID are accepted successfully but aren't delivered during the 5-minute deduplication interval.

### Message Grouping

[`MessageGroupId`](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_SendMessage.html) is the tag that specifies that a message belongs to a specific message group. Messages that belong to the same message group are always processed one by one, in a strict order relative to the message group (however, messages that belong to different message groups might be processed out of order).

![[Pasted image 20240206223252.png]]