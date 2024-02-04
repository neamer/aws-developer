Network Load Balancers (NLB) are Layer 4 load balancers that allow you to:
- Forward TCP & UDP traffic to your instances
- Handle millions of requests per seconds
- Less latency ~ 100ms (vs 400ms for ALB)

NLB has one static IP per AZ, and supports assigning Elastic IP

NLB are used for extreme performance, TCP or UDP traffic

NOTE: NLB are not included in AWS free tier

Health checks support the TCP, HTTP and HTTPS protocols

### Target groups

- EC2 instances
- IP Addresses - must be private IPs
- Application load balancer