Amazon Simple Notification Service (Amazon SNS) is a managed service that coordinates and manages the delivery or sending of messages to subscribing endpoints or clients.

In Amazon SNS, there are two types of clients—publishers and subscribers—also referred to as producers and consumers.

Publishers communicate asynchronously with subscribers by producing and sending a message to a topic, which is a logical access point and communication channel. 
Subscribers (web servers, email addresses, Amazon SQS queues, Lambda functions) consume or receive the message or notification over one of the supported protocols when they are subscribed to the topic.

**SNS supports a many-to-many model pub-sub where we can have multiple publishers and multiple subscribers by topic**.

![[Pasted image 20240208193418.png]]
*Examples of possible subscribers to SNS topics*

![[Pasted image 20240208193518.png]]
Examples of possible SNS publishers

We have two main ways of publishing to SNS:

Topic Publish (using the AWS SDK), we can:
- create a topic
- subscribe to a topic
- publish to a topic

Direct Publish (for the mobile apps SDK) - **used for push notifications**
- This woks by creating a "platform application" - which is a object for managing one of the supported push notification services to which devices and mobile apps may register.
- Then we can register the device for push notifications with a "platform endpoint".
- And then we can publish to the platform endpoint to send push notifications to mobile devices

# Security

**Encryption**:
- In-flight encryption using HTTPS API
- At-rest encryption using KMS keys
- Client-side encryption if the client wants to perform encryption/decryption themselves

**Access Controls**: IAM policies are used to regulate access to the SNS API

**SNS Access Policies**:
- Useful for cross-account access to SNS topics
- Useful for other services (ex. S3) to write to a SNS topic

# Message Filtering

By default, an Amazon SNS topic subscriber receives every message that's published to the topic. To receive only a subset of the messages, a subscriber can assign a _filter policy_ to the topic subscription.

A filter policy is a JSON object containing properties that define which messages the subscriber receives. Filter policies assume that the message payload is a well-formed JSON object.

![[Pasted image 20240208230344.png]]
*In this example we have a SNS topic which receives information about orders, and we have many queues and Email subscription event which receive only the subset of messages that they need.*