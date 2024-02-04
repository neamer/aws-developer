We can use AWS Lambda functions to change the object before it is retrieved by the caller application

Only one S3 bucket is needed, on top of which we create S3 Acces Point and S3 Object Lambda Access Points

Use cases:
- Redacting 

### Example

![[Pasted image 20240118161416.png]]

*In this example we have one S3 bucket which is owned by an E-commerce application. We have a analytics applications which should only get limited information. To provide this we can create a **Supporting S3 Access Point** which is accessed by a Redacting Lambda Function and then it is connected to the **S3 Object Lambda Access Point**. This analytics application is going to access the same data from the original bucket using this Lambda access point. We also need to supply a marketing application with enriched object. To do this, we have a the exact same setup, but our Lambda function will enrich the objects using a customer loyalty database instead.*