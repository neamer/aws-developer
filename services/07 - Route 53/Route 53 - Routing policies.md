Define how Route 53 responds to DNS queries

Don't get confused by the way the "Routing" is used, it is not the same way a Load Balancer routes traffic. DNS don't route traffic, it only responds to DNS queries.

Route 53 Supports the following routing policies:
- Simple
- Weighted
- Failover
- Latency based
- Geolocation
- Multi-Value Answer
- Geoproximity (using Route 53 Traffic Flow feature)

# Types of routing policies

### Simple

Simple routing is typically used to route traffic to a single resource. We can still specify multiple values in the same record

**If multiple values are returned, a random one is chosen by the client.**

When Alias is enabled, we can only specify one AWS resource.

Simple routing can't be associated with Health checks

![[Pasted image 20231230142245.png]]

### Weighted

Control the percentage of requests that go to each specific resource using weights.

When assigning a relative weight to a resource:
- The percentage of traffic to that record will be equal to the weight for that record divided by the sum of all weights for all records
- Weights don't need to sum up to 100

Note that:
- DNS records must have the same name and type
- Can't be associated with health checks

**Assigning a weight of 0 to a resource will stop sending traffic to it.**

**If all records have a weight of 0 then all records will have an equal chance of being returned**

![[Pasted image 20231230142854.png]]


### Latency-based

Redirects to the resource that has the lowest latency

**Latency is based on traffic between users and AWS regions**

Can be associated with health checks

![[Pasted image 20231230143307.png]]


# Failover

For failover records we need a primary and secondary instance and a health check of primary instance. If the health check is unhealthy then the DNS will resolve to the secondary instance

**Note that there can only be one primary and one secondary instance.**

![[Pasted image 20240101230736.png]]


# Geolocation

We can specify location by continent, country or US State (if there is overlapping then the most precise location is selected).

The DNS will resolve the IP to a matching location record if it is available, if it isn't then it will return the default record.

Use cases:
- website localization
- content distribution
- load balancing

Can be associated with health checks


![[Pasted image 20240101231121.png]]


# Geoproximity

Route traffic to your resources based on the geographic location of users and location **with the ability to shift traffic to resources based on the defined bias.**

To change size of the geographic region, specify bias values.
- To expand (1 to 99) - more traffic to the resource
- To expand (-1 to -99) - less traffic to the resource

Resources can be:
- AWS Resources (need to specify AWS region)
- Non-AWS Resources (need to specify latitude and longitude)

### Example

Lets take a look at this example of two records in USA, one is located in us-west-1 and the other in us-east-1 and both have a bias of 0.

![[Pasted image 20240101232012.png]]

The users will be routed to the record which is closest to their location and the (imaginary) dividing line will be in the center.

By adding bias to one of the records, we can change the routing without changing our setup.

![[Pasted image 20240101232430.png]]

In this case the diving line will be pushed to the west and more users will be routed to the us-east-1 instance.

### Traffic Flow

**We need to use Route 53 Traffic Flow (advanced) to use this feature.**

Traffic flow is a visual tool for editing routing policies

![[Pasted image 20240101232902.png]]

Example of a Geoproximity map in traffic flow.

**To conclude, geoproximity routing is very helpful when we need to easily be able to shift load from one region to another.**


# IP-based

Allows us to do routing based on the clients IP address by providing sets of [[CIDR]] Blocks and corresponding endpoints/locations

![[Pasted image 20240101233723.png]]

# Multi-Value

Used when routing traffic to multiple resources.

Route 53 will return multiple values/resources.

Can be associated with Health Checks so that only healthy resources are returned (main difference from simple routing).

Up to 8 resources can be returned for each query.

Multi value is not a substitute for having an ELB, the idea is that the client load balances on their end.
