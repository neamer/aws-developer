Access points provide us with a way to simplify security management for S3 buckets  by moving authorization outside of S3 bucket policies.

Each access point has:
- its own DNS name (Internet Origin or VPC origin)
- an access point policy (similar to bucket policy) - manage security at scale

![[Pasted image 20240118160511.png]]

In this example, we have multiple groups that need to access different data in our S3 bucket. We can create a S3 bucket policy but it would grow and become unmanageable over time.

We can create access points for each group and define the authorizations using access point policies. This way each policy is responsible for its security and it greatly simplifies security

# VPC Origin

We can define the access point to be accessible only from the VPC

In order to connect to the access point from our VPC, we must create a VPC endpoint.

The VPC endpoint policy must be configured to allow access to the target bucket and Access point

![[Pasted image 20240118161004.png]]
