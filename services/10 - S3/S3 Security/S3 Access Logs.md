Any request made to S3, from any account, authorized or denied will be logged into another S3 bucket.

The data can be analyzed using data analysis tools

The target bucket must be in the same AWS region

The log format is available at https://docs.aws.amazon.com/AmazonS3/latest/userguide/LogFormat.html

**It is very important to remember not to set your logging bucket to be the monitored bucket** because it will create a logging loop and the bucket will grow exponentially.