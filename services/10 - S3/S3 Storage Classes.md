In order to compare different storage classes, we should firstly define some concepts:

**Durability** is used to measure the likelihood of data loss. AWS measures durability as a percentage. For example, the S3 Standard Tier is designed for 99.999999999% durability. This means that if you store 100 billion objects in S3, you will lose one object at most.

**Availability** measures how readily available a service is. Availability is typically measure as a percentage. For example, the service level agreement for S3 is that it will be available 99.99% of the time which means that in a year it may be down up to 53 minutes.

# S3 Standard - General purpose

99.99% availability

Used for frequently accessed data

Low latency and high throughput

Can sustain 2 concurrent facility failures

Use cases:
- Big data analytics
- Mobile & gaming applications
- Content distribution

# S3 Infrequent access

For data that is less frequently accessed but requires more rapid access when needed

Lower cost than S3 Standard but you will have a cost on retrieval

**Amazon S3 Standard-Infrequent Access**
- 99.9% availability
- Use cases:
	- Disaster recovery
	- Backups

**Amazon S3 One Zone - Infrequent Access**
- Offers high durability (99.999999999%) in a single AZ **but data gets lost when AZ is destoyed.**
- 99.5% availability
- Use cases:
	- Storing secondary backup copies of on-premises data
	- Storing data you can recreate

# S3 Glacier Storage

Low-cost object storage meant for archiving / backup

Pricing: Object storage + object retrieval cost

**Amazon S3 Glacier Instant Retrieval**
- Millisecond retrieval, great for data accessed once a quarter
- Minimum storage duration of 90 days

**Amazon S3 Glacier Flexible Retrieval** (formerly Amazon S3 Glacier)
- Classes:
	- Expedited (1 to 5 minutes)
	- Standard (3 to 5 hours)
	- Bulk (5 to 12 hours) - free
- Minimum storage of 90 days

**Amazon S3 Glacier Deep Archive** - for long term storage
- Classes:
	- Standard (12 hours)
	- Bulk (48 hours)
- Minimum storage duration of 180 days

# S3 Intelligent-Tiering

Moves objects automatically between Access Tiers based on usage. There is a small monthly monitoring and auto-tiering fee but there are no retrieval charges in S3 Intelligent-Tiering.


- Frequent Access tier (automatic): default tier
- Infrequent Access tier (automatic): objects not accessed for 30 days
- Archive Instant Access tier (automatic): objects not accessed for 90 days
- Archive access tier (optional): Configurable from 90 days to 700+ days
- Deep Archive Access tier (optional): Configurable from 180 days to 700+ days



# Comparison of storage class options

![[Pasted image 20240110154505.png]]

# Comparison of storage class pricing

![[Pasted image 20240110154605.png]]

*Note that this was taken for eu-east-1 at the time of recording and may be out od date*