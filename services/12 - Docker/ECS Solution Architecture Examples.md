
# ECS tasks invoked by Event Bridge

![[Pasted image 20240131160050.png]]

We have a ECS Cluster backed by Fargate and a S3 bucket. EventBridge is configured to Run ECS tasks when objects are uploaded to the bucket. The tasks are configured to read the object from the bucket, process it and the save it to DynamoDB. **This will give us a serverless image processing setup.**

# ECS tasks invoked by EventBridge Schedule

![[Pasted image 20240131160515.png]]

In this example we have a ECS Cluster backed by Fargate. We configured EventBridge to run a ECS task every hour. The Task will have a ECS Task Role to access a S3 bucket. Then it can perform batch processing on it. **This is a example of a serverless structure for performing batch processing.**

# SQS Queue Example

![[Pasted image 20240131160812.png]]

In this example we have a SQS queue which will receive messages. We set up a ECS Cluster with ECS Service Auto Scaling to poll the queue for messages. The more messages that we have in the queue, the more tasks will be created.

# Intercept Stopped Tasks using EventBridge

![[Pasted image 20240131161051.png]]

In this example we have a ECS Cluster running multiple ECS tasks. Whenever a task is exited, it will register as a event on EventBridge which will alert a SNS topic to send an email to a Administrator.