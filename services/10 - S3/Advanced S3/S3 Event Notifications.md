Amazon S3 Event Notifications allow us to react to events (like S3:ObjectCreated, S3:ObjectRemoved...) by sending a notification to one of the following destinations:
- SNS Topic
- SQS Queue
- Lambda function

# Permissions

In order to be able to send S3 event notifications, we will need to define Access Policies.

![[Pasted image 20240117162847.png]]

All notifications sent by this service will end up in EventBridge.