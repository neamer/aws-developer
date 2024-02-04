If you want to distribute paid shared content to premium users we can use CloudFront Signed URLs/Cookies

We attach a policy with:
- URL Expiration
- IP ranges to access data from (useful if we know the client address)
- Trusted signers (which AWS accounts can create the signed URLs)

Then we will have to decide how long it will be valid for
- For shared content (movies, music) we should make it short (a few minutes)
- For private content we can make it last for years

Signed URLs allow access to **individual** files (one signed URL per file)

Signed Cookies allow access to **multiple** files (one signed cookie for many files)

![[Pasted image 20240125214342.png]]

*In this scenario we set up OAC so that Amazon CloudFront can only access our Amazon S3 bucket and we made it mandatory for our CloudFront distribution to be accessed with signed URLs. Here we would task our application with generating signed URLs and then supplying them to the clients to use with requests to CloudFront.*

### CloudFront Signed URL vs S3 Pre-Signed URL

**CloudFront Signed URL**
- Allow access to a path, no matter the origin
- Account wide key-pair, only the root can manage it
- Can filter by IP, path, date, expiration
- Can leverage caching features

![[Pasted image 20240125214816.png]]

**S3 Pre-Signed URL**
- Issue a request as the person who pre-signed the URL
- Uses the IAM key of the signing IAM principle
- Limited lifetime

![[Pasted image 20240125214926.png]]

# Signed URL process

We have two types of signers:
- **Trusted key group** (recommended option) - Leverage APIs to manage and rotate keys (using IAM for security). We create trusted key groups for CloudFront distributions and then we generate public and private keys. The private key is used by our applications to sign URLs and the public key is used by CloudFront to verify URLs
- An AWS account that contains a CloudFront Key Pair - For this method we need to use the root account and the AWS Console. **This is not recommended anymore because of the need for using the root account**