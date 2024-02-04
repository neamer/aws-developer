Health checks are mainly used to provide automated DNS failover

- Health checks that monitor an endpoint (application, server, other AWS resource)
- Health checks that monitor other health checks (Calculated Health Checks)
- Health checks that monitor CloudWatch alarms


### Monitoring an endpoint

Around 15 global health checkers will check the endpoints health
- Healthy/Unhealthy threshold - 3 (default)
- Interval - 30 sec (can be set to 10 sec with higher cost)
- Protocols: HTTP, HTTPS and TCP
- If >18% health checkers report that the endpoint is healthy then Route 53 considers it **healthy**. Otherwise it is deemed **unhealthy**
- You have the ability to choose the locations for the health checks

Health checks only pass when the endpoint responds with 2xx or 3xx status codes

Health checks can be setup to fail / pass based on the text in the first 5120 bytes of the response.

An important thing during setup is to configure our router/firewall to allow incoming requests from Route 53 Health Checkers

### Calculated health check

used to combine the results of multiple health checks into a single health check.

Up to 265 Child health checks can be monitored.

We can specify the number of passing health checks to make the parent pass.

A common use case is during website maintenance 


### Health checks for private zones

Route 53 health checkers are outside the VPC and they can not access private endpoints

Instead, we can create a **CloudWatch Metric** and associate a **CloudWatch Alarm** and then create a health check that checks the alarm itself.