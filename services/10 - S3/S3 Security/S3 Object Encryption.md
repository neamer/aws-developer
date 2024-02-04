
# Server-Size Encryption (SSE)


## Server-Size Encryption with Amazon S3-Managed Keys (SSE-S3)

Encrypts S3 objects using keys handled, managed and owned by AWS

Encryption type is **AES-256**

Must set header `"x-amz-server-side-encryption"` : `"AES256"`

**Enabled by default for new buckets & objects**

![[Pasted image 20240118145804.png]]


## Server-Size Encryption with KMS Keys stored in [[AWS KMS]] (SSE-KMS)

Instead of relying on the keys managed by S3 service, we manage our own keys using the [[AWS KMS]]

The advantage of this approach is that we have control of the keys and we can audit key usage using CloudTrail

Must set header `"x-amz-server-side-encryption"` : `"aws:kms"`

![[Pasted image 20240118145823.png]]

To read a file from the S3 bucket, not only do you need to be able to access the object itself, but also the KMS key that was used to encrypt the object

#### SSE-KMS Limitation

If you use SSE-KMS, you may be impacted by the KMS limits.

Whenever you upload, it calls the **GenerateDataKey** KMS API and when you download it calls the **Decrypt** KMS API. Each of these API calls is going to count towards the KMS quota per second (5500, 10000, 30000 req/s based on region)

Therefore, **if you have a very high throughput application that uses KMS SSE-KMS you may end up throttling.**


## Server-Size Encryption with Customer-Provided Keys (SSE-C)

Server-Side Encryption using keys fully managed by the customer outside of AWS

Amazon S3 does NOT store the encryption key you provide, they are discarded after use

**HTTPS must be used** and we must pass the encryption key in HTTP headers for every request.

![[Pasted image 20240118150837.png]]


# Client-Side Encryption

The idea is that the client has to encrypt the data themselves before sending it to S3 and decrypt it when retrieving it from S3. Therefore, the client fully manages the keys and encryption cycle.

It is must easier to implement using **Amazon S3 Client-Side Encryption Library**

![[Pasted image 20240118151033.png]]


# Encryption in Transit (SSL/TLS)

Encryption in transit (flight) is also called SSL/TLS

Amazon S3 exposes two endpoints:
- **HTTP Endpoint** - non encrypted
- **HTTPS Endpoint** - encryption in flight

**HTTPS is recommended**
**HTTPS is mandatory for SSE-C**

This is usually not a problem because most clients use HTTPS by default.

##### Forcing encryption in transit

We can force encryption in transit by attaching a bucket policy to your S3 bucket which checks for the **aws:SecureTransport** condition.

SecureTransport is going to be true whenever using HTTPS

![[Pasted image 20240118151730.png]]

# Force encryption

We can force encryption by using a bucket policy and refuse any API call to PUT an S3 object without encryption headers (SSE-KMS or SSE-C)

![[Pasted image 20240118152659.png]]
*examples*