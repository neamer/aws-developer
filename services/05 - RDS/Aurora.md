Amazon Aurora is a proprietary technology from AWS

PostgreSQL and MySQL are both supported as Aurora DB drivers.

Aurora is "AWS cloud optimized" and claims:
- 5x performance improvement over MySQL on RDS
- over 3x the performance of Postgres on RDS

Aurora storage automatically grows in increments of 10GB, up to 128TB

Aurora can have up to 15 replicas and the replication process is faster than MySQL (sub 10 ms replica lag)

Failover in Aurora is instantaneous, It's [[High availability]] native.

**Aurora costs more than RDS (20% more) - but it is more efficient**

## High availability and Read Scaling

Any time you store anything on your DB, Aurora will store 6 copies of your data across 3 AZ (2 instances on each).

Like in regular RDS, only one instance is regarded as master, and there is automated failover in less than 30 seconds.

In case of failure, Aurora only needs:
- 4 copies out of 6 for write operations
- 3 copies out of 6 for read operations
That means that we are fine if a AZ fails.

Aurora supports self healing with peer-to-peer replication.

You do not rely on one volume, storage is striped across 100s of volumes

Like in RDS, we can have up to 15 Aurora Read Replicas to serve reads. But in Aurora we can also have Auto Scaling for Read Replicas

Aurora also has support for Cross Region Replication

## Aurora DB Cluster

The cluster provides us with two endpoints:
- **Writer Endpoint** which always points to the master and is used for read-write operations
- **Reader Endpoint** which has a load balancer that will connect you to one of the read replicas (The load balancing happens at the connection level and not the statement level)

![[Pasted image 20231128224423.png]]