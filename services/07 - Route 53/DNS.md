A Domain Name System translates the human friendly hostnames into machine IP address

www.google.com => 172.217.1.52

DNS uses hierarchical naming structure

=============== less precise
.com
example.com
api.example.com
www.api.example.com
=============== more precise


### Terminology

**Domain Registrat**: Amazon Route 53

**DNS Records**: A, AAAA, CNAME, NS

**Zone File**: contains DNS records

**Name server**: Resolves DNS queries (Authoritative or Non-Authoritative)

**Top Level Domain (TLD)**: .com, .us, .in, .gov

**Second Level Domain (SLD)**: amazon.com, google.com

# URL Anatomy

![[Pasted image 20231228190420.png]]



# How DNS Works

![[Pasted image 20231228190715.png]]


In this example we have a web server with the address example.com that we want to access using our Web browser.

In order to obtain the IP address we are going to query our Local DNS Server. If it does not have the result in the cache it is going to query the Root DNS Server.

The Root DNS Server is going to give our Local DNS Server the address of the NS where we should look next. This is going to be the .com TLD DNS Server.

When our Local DNS Server queries the .com TLD DNS Server it is going to forward us to the SLD SN where we should look next. In this example that is the example.com SLD DNS Server. Finally, our local DNS server is going to get the IP that we needed and it is going to save it in its cache with a TTL in case we need it again shortly.