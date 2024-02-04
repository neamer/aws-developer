VPC Endpoints allow you to connect to AWS Servies **using a private network** instead of the public www network.

This provides enhanced security and lower latency to access AWS services.

We use two types of endpoints depending on the service:
- VPC Endpoint Gateway - S3 & DynamoDB
- VPC Endpoint Interface - all other services

![[Pasted image 20240104120945.png]]

**To summarize, VPC endpoints are really helpful for getting private access from within your VPC to an AWS service. Therefore, whenever the exam asks us to privately connect to a AWS service, VPC Endpoint will be the answer**

