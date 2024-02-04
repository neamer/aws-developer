EFS (Elastic file system) is a managed NFS(Network file system) that can be mounted on many EC2 instances

EFS works with EC2 instances in multiple AZ

Highly available, scalable and expensive (2x gp2), pay per use

Use cases:
- Content management
- Web serving 
- Data sharing
- Wordpress

Uses NFSv4.1 protocol

Uses security groups to control access

Encryption at rest uses KMS

Compatible with Linux-based [[AMI]]

POSIX file system that has a standard file API

File system scales automatically, pay-per-use, no planning

### EFS Performance classes

EFS Scale

Performance mode
- General purpose (default) - latency sensitive use-cases (web server, CMS)
- Max I/O - higher latency, throughput, highly parallel (big data, media processing)

Throughput mode
- Bursting - improvement in throughput as storage increases
- Provisioned - set your throughput regardless of storage size
- Elastic - automatically scales throughput up or down based on your workloads

### EFS Storage classes

**Storage tiers:**
- Standard - for frequently accessed files
- Infrequent access (IA) - cost to retrieve files, lower price to store

*Lifecycle management features allow us to move files to infrequent access after N days.*

**Availability and durability:**
- Standard - Multi AZ, great for prod
- One zone - Great for dev, backup enabled by default, compatible with IA (Infrequent Access) for more aggressive cost saving measures