Amazon Route 53 is a highly available, scalable, fully managed, authoritative DNS.
*Authoritative = the customer (you) can update the DNS records*

Route 53 is also a domain registrar.

It is the only AWS service that provides 100% availability SLA.

*53 is a reference to the traditional DNS port*

![[Pasted image 20231228191536.png]]

# Records

Records are rules for how you want to route your traffic for a domain

Each record contains:
- Domain/subdomain name - e.g. example.com
- Record Type - e.g. A, AAAA
- Value - e.g. 12.34.56.78
- Routing Policy - How Route 53 will respond to queries
- TTL - Amount of time the record is cached at DNS Resolvers

# Record Types

The following are the DNS record types that must be known for the exam:
- **A** - maps a hostname to IPV4
- **AAAA** - maps a hostname to IPV6
- **CNAME** - maps a hostname to another hostname
	- The target is a domain name which must have a A or AAAA record
	- Can't create a CNAME record for the top node of a DNS namespace (Zone Apex)
- **NS** - Name servers for the Hosted Zone
	- Control how traffic is routed for a domain

### Hosted Zones

Hosted Zones are containers for records that define how to route traffic to a domain and its subdomains

**Public Hosted Zones** - contains records that specify how to route traffic on the internet (public domain names)
**Private Hosted Zones** - contain records that specify how to route traffic within one or more VPCs (private domain names)

![[Pasted image 20231228192816.png]]
*Public Hosted Zone example*


![[Pasted image 20231228192849.png]]
*Private hosted zone example*

# CNAME vs Alias

Lets say we are using a ELB which exposes the AWS hostname lbl123samdfgml.elb.amazon.aws.com and you want to use the hostname myapp.domain.com

With a CNAME record we can point a specific hostname to any other hostname and with this we can achieve our desired effect. **NOTE that this can only be done for non-root domains (myapp.domain.com and NOT domain.com)**

An Alias points a hostname to a specific AWS resource and we can achieve the desired effect with this as well. Unlike CNAME, this method works for root domains
It is also:
- free of charge and
- provides native health checks

# Alias Records

Alias records map a hostname to a AWS resource.

They automatically recognize changes in the resource IP address.

Unlike CNAME, this method works for the top node of a DNS namespace (Zone apex)

Alias records are always of type A/AAAA for AWS resources (IPv4/IPv6)

You can't set the TTL

Possible alias targets are:
- ELB
- CloudFront distributions
- API Gateway
- Elastic Beanstalk environment
- S3 Websites
- VPC Interface Endpoints
- Global Accelerator
- Route 53 Records in the same hosted zone

**You cannot set an alias for an EC2 DNS name**