An ELB (Elastic Load Balancer) is a AWS-managed Load Balancer, which means that AWS:
- Guarantees that it will be working 
- Takes care of upgrades, maintenance, high availability
- Provides you (limited) configuration options

It costs less to set up your own load balancer but it will take much more effort.

### Health checks

They enable the load balancer to know if instances are available to reply to requests.

It works by sending a HTTP request to the application (usually /health) and if the response code is different from 200, then the instance is deemed unhealthy.

### Types of ELB

There are 4 managed types of load balancers on AWS:
- CLB (Classic Load Balancer) - v1, old generation - 2009
	- HTTP, HTTPS, TCP, SSL
- [[ALB]] (Application Load Balancer) - v2, new generation - 2016
	- HTTP, HTTPS, WebSocket
- [[NLB]] (Network Load Balancer) - v2, new generation - 2017
	- TCP, TLS (Secure TCP), UDP
- [[GWLB]] (Gateway Load Balancer) - Operates at layer 3 - IP Protocol

CLB are marked as deprecated and it is recommended to use the newer ones.

Some load balancers can be setup as internal (private) or external (public)

### Security groups

The usual setup is to allow HTTP / HTTPS traffic from anywhere to the load balancer, and then setup the EC2 security group so that only traffic from the load balancer is allowed.