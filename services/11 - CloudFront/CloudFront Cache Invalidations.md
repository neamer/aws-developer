CloudFront is not immediately aware of changes made to our back-end origin. It will only get the refreshed content after the TTL has expired.

If we don't want to wait for the TTL to expire, we can force a partial or full cache refresh by performing a **CloudFront Invalidation.**

We can invalidate all files or only files with a special path (e.g. /images/*)

![[Pasted image 20240125204748.png]]

*Example of a Cache Invalidation. The admin user (blue) will update the files and then perform invalidations for /index.html and /images/. Then when the end user (orange) performs a request, the edge location will get the original item from the origin.*