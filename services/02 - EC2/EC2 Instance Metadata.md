**AWS EC2 Instance Metadata (IMDS)** is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into [categories](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-categories.html), for example, host name, events, and security groups.

The URL for accessing this data is `http://169.254.169.254/latest/meta-data`

# Versions

You can access instance metadata from a running instance using one of the following methods:

- Instance Metadata Service Version 1 (IMDSv1) – a request/response method
- Instance Metadata Service Version 2 (IMDSv2) – a session-oriented method

### IMDSv1

with IMDSv1 we can access `http://169.254.169.254/latest/meta-data` directly without the need for authentication

### IMDSv2

IMDSv2 is more secure and is done in two steps:

 1. Get session token (limited validity) - using headers & PUT
```bash
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`
```

2. Use session token in IMDSv2 calls using headers
```bash
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/instance-id/
```
