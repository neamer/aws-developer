RDS Multi AZ is mainly used for disaster recovery

It works by synchronously replicating every change on the DB to a RDS instance in another AZ.

We get one DNS name, and in case of a problem with the master DB (loss of AZ, loss of network, instance or storage failure) there is a automatic failover to the standby DB.

![[Pasted image 20231128221322.png]]


**Common exam question:**
A [[RDS Read Replica]] can be setup as Multi AZ for Disaster Recovery (DR)


# From Single-AZ to Multi-AZ

Going from Single-AZ to Multi-AZ is a **zero downtime operation**(no need to stop the DB)

The following steps happen internally:
1. A snapshot is taken
2. A new DB is restored from the snapshot in a new AZ
3. Synchronization is established between the two databases