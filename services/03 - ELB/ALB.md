Application Load Balancer is a Layer 7 (HTTP) load balancer that provides load balancing to multiple HTTP applications across machines (target groups)

Load balancing to multiple applications on the same machine.

Support for HTTP/2 and WebSocket.

Supports redirects (from HTTP to HTTPS for example)

### Routing tables to different target groups

Routing based on path in URL (example.com/users & example.com/posts)

Routing based on hostname in URL (one.example.com & two.example.com)

Routing based on query string, headers (example.com/users?id=1&order=false)

ALB are a great fit for micro services & container-based applications

Has a port mapping feature to redirect to dynamic ports in ECS

Example:
![[Pasted image 20231125235636.png]]

### Target groups

EC2 Instances (can be managed by a auto-scaling group) - HTTP

ECS tasks (managed by ECS itself) - HTTP

Lambda functions - HTTP request is transferred to a JSON event

IP addresses - must be private IPs

ALB can route to multiple target groups

Health checks are at target group level


![[Pasted image 20231125235955.png]]
*Load balancing by splitting mobile and desktop traffic based on query string*

### Good to know

- Fixed hostname (XXX.region.elb.amazonaws.com)
- The application servers don't see the IP of the client directly
	- The true IP of the client will be inserted in the header X-Forwarded-For
	- We can also get the port from X-Forwarded-Port and protocol X-Forwarded-Proto