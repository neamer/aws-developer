Amazon RDS Proxy provides a fully managed database proxy for RDS.

It allows apps to pool and share DB connections established with the database

**Improves database efficiency by reducing the stress on database resources (e.g. CPU, RAM) and minimize open connections (and timeouts)**

It is serverless, autoscaling and higly available (multi-AZ)

**Reduces RDS & Aurora failover time by 66%**

Supports:
- RDS
	- MySQL
	- PostgreSQL
	- MariaDB
	- MS SQL Server
- Aurora
	- MySQL
	- PostgreSQL

It also provides a easy way to **enforce IAM Authentication for DB, and securely store credentials in the AWS Secrets Manager**

**RDS Proxy is never publicly accessible (must be accessed from VPC)**

One of the main use cases for RDS proxies is Lambdas.

Since lambdas can multiply, they pose the risk of overloading our database connections, RDS proxy pools these connections and solves the issue.