Amazon Simple Queue Service (Amazon SQS) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components.

Anything that sends messages into the queue is called a **producer** and there can be multiple producers per queue. Then, an application needs to receive the messages, process them and then delete them from the queue. These applications are called **consumers**, and there can be multiple consumers per queue.

**Anytime you see decoupling mentioned in your exam, immediately think SQS.**

Main characteristics:
- Unlimited throughput, meaning you can send as many messages/second as you need
- Unlimited number of messages in queue
- Default retention of messages is 4 days, maximum is 14
- Low latency (<10 ms on publish and receive)
- Small message size (limit of 256 KB)

Caveats to using SQS:
- SQS has [[At least once delivery]], meaning it can occasionally deliver the same message twice.
- Can have out of order messages

##### Producing messages

1. Messages are produced to SQS using the AWS SDK with the **SendMessage API**.
2. The message will then be persisted in the queue until a consumer deletes it

##### Consuming messages

Consumers can be running on EC2 instances, running on our own on-premises servers or on AWS Lambda

1. The consumers will poll the queue for messages. They can receive up to 10 at a time
2. After receiving a message, the consumer will be responsible for processing it.
3. Then, the consumer will delete the processed messages using the **DeleteMessage API** 

If we want to scale throughput of processing, we can horizontally scale the consumers

### Example: SQS with ASG

![[Pasted image 20240205223131.png]]

*In this example we want to scale the consumer EC2 instances when the number of messages in our SQS queue reaches a certain threshold. We can do that with a CloudWatch Metric called ApproximateNumberOfMessages. We then send a CloudWatch Alarm to our ASG to scale it up.*

### Example: SQS to decouple applications

Let's say that we need a application that needs to process videos and then save them to a S3 bucket.

Instead of doing this in a monolithic way with a single application (which has the potential to slow down during processing) we can leverage a separate backend and SQS queue to decouple the applications.

![[Pasted image 20240205223715.png]]

This approach also let's us choose specialized instance tiers to suit our processing needs and also lets us have more control over our scaling.

# SQS Security

For encryption, we have the following options:
- In-flight encryption using HTTPS API
- At-rest encryption using KMS keys
- Client-side encryption if the client wants to perform encryption / decryption themselves

For Access Policies: IAM policies can be used to regulate access to SQS API

We also have [[SQS Access Policies]]