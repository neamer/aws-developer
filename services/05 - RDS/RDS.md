Relational Database Service is a AWS managed DB service for SQL-based databases.

It allows you to create databases in the cloud that are managed by AWS. 
The following DB engines are supported:
- PostgreSQL
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- [[Aurora]] (AWS Proprietary database)

##### Advantage of RDS over DB on EC2

RDS is a managed service:
- Automatic provisioning, OS patching
- Continuous backups and restore to specific timestamp (Point in Time Restore)
- Monitoring dashboards
- Read replicas for improving read performance
- Multi AZ setup for DR (Disaster Recovery)
- Maintenance windows for upgrades
- Scaling capability (vertical and horizontal)
- Storage backed by EBS (gp2 or io1)

**You can't SSH into your instances**

### Storage Auto Scaling

Helps you increase storage on your RDS DB instance dynamically

When RDS detects you are running out of free database storage, it scales automatically.

You only have to set the **Maximum storage threshold** (maximum limit for DB storage)

The storage will be modified if:
- Free storage is less than 10% of allocated storage
- Low-storage lasts at least 5 minutes
- 6 hours have passed since last modification

Supports all RDS DB engines