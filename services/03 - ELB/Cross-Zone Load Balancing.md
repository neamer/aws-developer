Cross-Zone Load Balancing allows us to balance traffic evenly across all instances in multiple AZs

![[Pasted image 20231126145352.png]]

**Application load Balancer ([[ALB]])**
- Enabled by default (can be disabled at Target Group level)
- No charges for inter AZ data

**Network Load Balancer ([[NLB]]) & Gateway Load Balancer ([[GWLB]])**
- Disabled by default
- You pay charges for inter AZ data if enabled

**Classic Load Balancer**
- Disabled by default
- No charges for inter AZ data if enabled