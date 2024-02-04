Amazon CloudFront is a Content Delivery Network (CDN)

It improves read performance by caching content at [[AWS Edge location]] (>216 points of presence globally)

In addition, CloudFront provides DDoS protection because it is worldwide. Integrates with Shield and AWS Web Application Firewall.

# Origins

An origin is **the location where content is stored, and from which CloudFront gets content to serve to viewers**.

Origins can be:
- **S3 Buckets** - This allows us to distribute and cache our S3 objects at edge locations. We get enhanced security with CloudFront Origin Access Control (OAC) *which is replacing Origin Access Identity (OAI)*. CloudFront can also be used as an ingress (entrypoint) to upload files to S3.
- **Custom origin (HTTP)** - Can be any custom origin backend such as:
	- [[ALB]]
	- [[EC2]] instance
	- S3 website
	- Any other HTTP backend you want


![[Pasted image 20240122213650.png]]*High level overview of how CloudFront works*


![[Pasted image 20240122213820.png]]
Overview of CloudFront with an S3 bucket as the origin.


# CloudFront vs Cross Region Replication

Common exam question

CloudFront
- Global Edge network and files are cached for a TTL (maybe a day)
- **Great for static content that must be available everywhere**

S3 Cross Region Replicaiton:
- Must be setup for each region you want replication to happen
- Files are updated in near real-time
- Read only
- **Great for dynamic content that needs to be available at low-latency in few regions**


# ALB or EC2 as an origin

![[Pasted image 20240125211220.png]]

To set an EC2 instance as a origin, it will have to be public because there is no VPC connectivity in CloudFront. We will also have to create a security group which allows the public IP addresses of Edge locations

![[Pasted image 20240125211502.png]]

We can have a public EC2 instance by setting a ALB as our origin. Then we will only need to configure the EC2 security group to allow the ALB. The ALB will have to be public and we will need to configure its security group to allow the public IP addresses of Edge locations.

# Geo Restriction

We can restrict who can access our distributions with
- **Allowlist**: Allow access only if the user is from a country on the list of approved countries
- **Blocklist**: Allow all access, except for users whose countries are on the blocklists

A common use-case is to satisfy copyright laws

# Real Time Logs

You can get real time requests received by CloudFront sent to Kinesis Data Streams

Monitor, analyze and take action on the content delivery performance

Allows you to choose:
- Sampling rate
- Specific fields and Cache behaviours to include (based on path patterns)