Here are some more advanced concepts that will be needed for the Certified Developer Exam

### Short and Long Polling

Amazon SQS provides short polling and long polling to receive messages from a queue. By default, queues use short polling.

With _short polling_, the [`ReceiveMessage`](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html) request queries only a subset of the servers (based on a weighted random distribution) to find messages that are available to include in the response. Amazon SQS sends the response right away, even if the query found no messages.

With _long polling_, the [`ReceiveMessage`](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/APIReference/API_ReceiveMessage.html) request queries all of the servers for messages. Amazon SQS sends a response after it collects at least one available message, up to the maximum number of messages specified in the request. Amazon SQS sends an empty response only if the polling wait time expires.

**Long polling decreases the number of API calls made to SQS while increasing the efficiency and decreasing the latency of your application**. Therefore, long polling is generally preferable to short polling

Long polling can either be enabled at the queue level or at the API level using the **ReceiveMessageWaitTimeSeconds** parameter.


### SQS Extended Client

You the can use the [Amazon SQS Extended Client Library for Java](https://github.com/awslabs/amazon-sqs-java-extended-client-lib) and S3 to manage large SQS messages. This is especially useful for consuming large message payloads, from 256 KB and up to 2 GB. 

![[Pasted image 20240206220255.png]]

The library saves the message payload to an S3 bucket and sends a message containing a reference of the stored S3 object to a SQS queue.

### Must know API

Here are some API calls that will be used throughout the exam

- **CreateQueue** (MessageRetentionPeriod) - is used to create a queue
	- *MessageRetentionPeriod* parameter to set the message retention.
- **DeleteQueue** - is used to delete a queue and all its messages
- **PurgeQueue** - deletes all messages in the queue
- **SendMessage** - sends message
	- *DelaySeconds* is a optional parameter
- **ReceiveMessage** is used for polling a queue, some parameters are: 
	- *MaxNumberOfMessages* is 1 by default, can be set to 10
	- *ReceiveMessageWaitTimeSeconds* is used for Long Polling
- **DeleteMessage** is used to remove a message from a queue after it has been processed by a consumer
- **ChangeMessageVisibility** changes the message timeout

You can use batch API calls for SendMessage, DeleteMessage, ChangeMessageVisibility to lower the number of API calls and decrease costs.