ElastiCache is essentially RDS for in-memory databases. It provides a simple AWS managed service for caches like Redis or Memcached.

Like for RDS, AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups.

**Helps make your application stateless**

**NOTE: Using ElastiCache requires heavy application code changes**

# Usage

### DB Cache

![[Pasted image 20231218215046.png]]

The application queries ElastiCache, if the query is not available then it gets the data from RDS and stores the result in ElastiCache.

### Session Store

![[Pasted image 20231218215214.png]]

Whenever a user logs in to the application, the session is stored in ElastiCache. When the user hits another instance of our application, the session is retrieved from the cache.

This approach leads to a stateless application.

# Redis vs Memcached

![[Pasted image 20231218215428.png]]