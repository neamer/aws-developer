
# Pricing

Since CloudFront [[AWS Edge location]]s are all around the world, the cost of data out per edge location varies

![[Pasted image 20240125215719.png]]
We can notice that the price is lower on the left and higher on the right

We can reduce the number of edge locations for cost reduction

We have three price classes:
- Price Class All: all regions - best performance
- Price Class 200: includes most regions, excludes the most expensive ones
- Price Class 100: only the least expensive regions

![[Pasted image 20240125215937.png]]

# Origin groups

With origin groups, we define a primary and a secondary origin to increase availability and to have failover incase the primary origin fails

![[Pasted image 20240125220210.png]]
*Region-level high availability with CloudFront Origin Groups*


# Field Level Encryption

Adds an additional level of security along with HTTPS to protect user sensitive information through the application stack.

Sensitive information is encrypted at the edge using asymmetric encryption

Usage:
1. Specify sets of fields in POST requests that you want encrypted (up to 10)
2. Specify the public key to encrypt them

![[Pasted image 20240125220559.png]]
*In this example we want to encrypt credit card information that is passed to our edge location. It will be encrypted with a public key and then the information will be passed through our entire stack to the web servers. They will have access to private keys with which they will be able to decrypt the information.*