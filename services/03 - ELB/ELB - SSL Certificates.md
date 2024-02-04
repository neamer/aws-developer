An SSL Certificate allows traffic between your clients and your load balancer to be encrypted in transit (in-flight encryption)

SSL refers to Secure Sockets Layer, used to encrypt connections
TLS refers to Transport Layer Security, which is a newer version
Nowadays, TLS certificates are mainly used, but people stil refer to them as SSL

Public SSL certificates are issued by Certificate Authorities (CA)

SSL certificates have an expiration date and must be renewed

The load balancer uses an X.509 certificate (SSL/TLS server certificate)

You can manage certificates using ACM (AWS Certificate Manager), or you can create and upload your own certificates alternatively.

For the HTTPS listener:
- You must specify a default certificate
- You can add an optional list of certs to support multiple domains
- Clients can use SNI (Server Name Indication) to specify the hostname they reach
- Has the ability to specify a security policy to support older versions of SSL / TLS (legacy clients)

# SNI - Server Name Indication

SNI solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites)

It's a 'newer' protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake.

The server will then find the correct certificate, or return the default one


NOTE:
- Only works for [[ALB]], [[NLB]] & Cloudfront
- Does not work for CLB

Therefore, we must use multiple CLB for multiple hostnames with multiple SSL certificates.

And for the newer generation, we can rely on SNI to make it work with one load balancer