### Network ACL

NACL (or Network Access Control List) is a Firewall which controls traffic from and to a subnet which:
- can have ALLOW or DENY rules
- Are attached at the subnet level
- Rules only include IP addresses

### Security groups

A Security Group is a firewall which controls traffic to and from an ENI / an EC2 instance

It can only have ALLOW rules

Rules include IP addresses and other security groups.

![[Pasted image 20240104114935.png]]
*Standard VPC setup diagram with NACL, Security group and an EC2 instance*

**NACL is our first line of defense and all traffic that comes to our instances will pass through it before Security group which is a second line of defense.**


![[Pasted image 20240104115156.png]]
*Detailed comparison of NACL and Security groups, NOT needed for the exam but good to know*