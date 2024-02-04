
Implementation considerations:

- **Is it safe to cache data?** Data will be eventually consistent
- **Is caching effective for the data?**
- **Is data structured well for caching**

# Lazy Loading / Cache-Aside / Lazy population

![[Pasted image 20231218222701.png]]

The application will firstly query ElastiCache. If we get a Cache miss, then we will query the DB and write the result to the cache.

Pros:
- Only requested data is cached (the cache isn't filled with unused data)
- Node failures are not fatal (just increase the latency to 'warm' the cache)

Cons:
- Cache miss penalty that results in 3 round trips, noticeable delay for that request
- Stale data: data can be updated in the database and outdated in the cache

NOTE: Cache warm up refers to a period where all request will be cache misses and all requests will need to go to RDS.

![[Pasted image 20231218223124.png]]
*Python pseudocode example for lazy loading*

# Write Through

![[Pasted image 20231218223516.png]]

Whenever there is a write happening on the application, the data is written on the DB and ElastiCache simultaneously.

Pros:
- Data in cache is never stale, reads are quick
- Write penalty vs Read penalty (each write requires 2 calls)

Cons:
- Missing Data until it is added / updated in the DB
- Cache Churn - a lot of the stored data will never be read

A possible mitigation for the missing data is to combine this method with lazy loading.

![[Pasted image 20231218224040.png]]
*Python pseudocode example for write through*

# Cache evictions

Cache eviction basically refers to removing items from the cache.

Cache eviction can occur in three ways:
- Explicitly deleting the item
- The memory is full and the item is **Least Recently Used (LRU)**
- You set an **Time To Live (TTL)**
