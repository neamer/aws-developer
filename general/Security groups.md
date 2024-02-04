Security groups act as a firewall to our instances

They regulate:
- Access to ports
- Authorized IP ranges
- Control of inbound network
- Control of outbound network

Security groups are completely separate from your instances. If traffic is blocked by the security group, the instance will not even see it.

**If your application is not accessible and the client gets a time out, then it is a security group issue.**

If you applicationE gets a connection refused error, then it is a application issue.

All inbound traffic is **blocked** by default
All outbound traffic is **allowed** by default

Other security groups can be referenced while defining behavior for a specific group.

**YOU ARE NOT EXPECTED TO KNOW HOW TO CONFIGURE A SECURITY GROUP FOR THE EXAM**