Gateway Load Balancers (GWLB) are Layer 3 (Network layer - deals with IP packets) load balancers that are used to deploy, scale and manage a fleet of 3rd party network virtual appliances in AWS.

Use cases:
- Firewalls
- Intrusion detection and prevention systems
- Deep packet inspection
- Payload manipulation

Combines the following functions:
- Transparent Network Gateway - single entry/exit for all traffic
- Load balancer - distributes traffic to your virtual appliances

**NOTE: Uses the GENEVE protocol on port 6081**

### Target groups

- EC2 instances
- IP Addresses - must be private IPs


### Example

![[Pasted image 20231126004215.png]]

In this scenario we have additional security appliances (ex. EC2 instances) which we want all traffic to go through before it reaches our destination application.

When traffic reaches the GWLB, it will send it to the target group and await a response.

If the target group accepts the traffic, then the GWLB forwards the traffic to the application.