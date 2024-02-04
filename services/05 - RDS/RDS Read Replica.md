Read replicas are used to scale reads

We can create up to 15 read replicas within AZ, cross AZ or even cross region

Replication is async, so reads are eventually consistent

Replicas can be promoted to their own DB

Read replicas are only used for SELECT statements.
## Use Cases

1. You have a production database that is taking on normal load, but you want to run a reporting application to run some analytics. By creating a read replica you can run the new workload without affecting the production application.

## Network Cost

In AWS there's a network cost when data goes from one AZ to another

**For RDS Read Replicas within the same region, you don't pay that fee**

![[Pasted image 20231128220938.png]]