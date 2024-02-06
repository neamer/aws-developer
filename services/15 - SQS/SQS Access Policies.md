SQS Access policies are JSON IAM policies (similar to S3 Bucket policies) that are added directly to your SQS queues.


# Use Cases

There are two main use cases for SQS queue policies that the exam will test you on:

#### Cross Account Access

If a consumer from another account needs to poll the queue for messages, then we will need to explicitly allow that action with a SQS Access Policy

![[Pasted image 20240206201811.png]]

The IAM policy would look like this:
![[Pasted image 20240206201830.png]]

#### Publish S3 Event Notifications to SQS Queue

![[Pasted image 20240206202008.png]]

In this case the S3 bucket will need explicit permissions to send messages to the SQS queue.

The policy would look something like this:
![[Pasted image 20240206202117.png]]