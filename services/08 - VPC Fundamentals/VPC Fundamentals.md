A VPC (Virtual Private Network) is a private network to deploy your resources (regional resource)

Subnets allow you to partition the network inside your VPC, and can be:
- Public - Accessible from the internet
- Private - Not accessible from the internet

**VPC is a regional resource and subnets are AZ resource**

To define access to the internet and between subnets, we use **Route Tables**

![[Pasted image 20240104102615.png]]
Diagram of a VPC with four subnets, across two AZs with the address range 10.0.0.0/16

# Internet Gateway

Internet gateways (IGW) helps our VPC instances connect with the internet.

Public subnets have a route to the internet gateway

![[Pasted image 20240104102939.png]]


# NAT Gateway

A NAT gateway is **a AWS-managed Network Address Translation (NAT) service**. You can use a NAT gateway so that instances in a private subnet can connect to services outside your VPC but external services cannot initiate a connection with those instances.

NAT instances serve the same function but are self-managed. 

![[Pasted image 20240104114103.png]]
Diagram of how a NAT connects the private subnet to the internet. The traffic is routed through a public subnet to a IGW.

# VPC Flow Logs

Any time we have traffic going through our VPC, it will be logged in our Flow Log.

- VPC Flow Logs
- Subnet Flow Logs
- Elastic Network Interface Flow Logs

Helps monitor & troubleshoot connectivity issues, e.g.:
- Subnets to internet
- Subnets to subnets
- Internet to subnet

Network information from AWS managed interfaces is captured as well: ELB, ElastiCache, RDS, Aurora, etc...

VPC FLow Logs data can go to S3, CloudWatch Logs, Kinesis Data Firehose

# VPC Connectivity

### Site To Site VPN

Connect a on-premises VPN to AWS

The connection is automatically encrypted

Goes over the public internet

### Direct Connect (DX)

Establish a physical connection between on-premises and AWS

The connection is private, secure and fast

Goes over a private network

Takes at least a month to establish

![[Pasted image 20240104121331.png]]