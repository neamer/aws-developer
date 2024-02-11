Amazon Data Firehose is a fully managed, serverless, automatically scaling service for delivering real-time streaming data.

Producers for Kinesis Data Firehose can be all the ones we mentioned for Kinesis Data Streams, but they can also be a Kinesis Data Streams stream, Amazon CloudWatch, AWS IoT.

Kinesis Firehose can optionally transform the data with a AWS Lambda function.

Data is written in batches to destinations.

There are three types of destinations for Kinesis Data Firehose:
- **AWS** (must know)
	- **[[S3]]**
	- **Amazon Redshift** - Data warehouse service (The data will first be written to S3 and then copied to Redshift)
	- **Amazon OpenSearch**
- 3rd-Party Partner Destinations (ex. Splunk, New Relic ...)
- Custom Destinations

Once the data is sent, we can optionally send the data to a S3 bucket for backup. We can also choose to only send failed data to a S3 bucket.

![[Pasted image 20240210203056.png]]

Kinesis Data Firehose buffers incoming data before delivering it to destinations. You can configure the values for buffer size (1 MB to 128 MB) or buffer interval (**60 to 900 seconds**), and the condition satisfied first triggers data delivery to the destination. Because of this, Kinesis Data Firehose processing is called ***near real-time***.

It also supports many data formats, conversions, transformations and compression.

# Kinesis Data Streams vs Firehose
Common exam question

![[Pasted image 20240210203652.png]]