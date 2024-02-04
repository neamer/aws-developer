
The typical Three Tier Architecture comes up very frequently during exam questions.

![[Pasted image 20240104121951.png]]

Firstly, we have a Public subnet with our ELB, since the ELB needs to be publicly available. In this example we are using Route 53 as the DNS.

The next subnet contains an ASG, which will only need to be accessed by our ELB, and therefore it will be a **private subnet**. The ELB will be able to communicate the subnet using a routing table. This subnet is commonly called the **compute subnet**.

Then we are going to have a second private subnet which will contain our data, this is called the **data subnet.** This subnet contains RDS and can also contain ElastiCache.