
Amazon S3 Security is divided into:

**User-Based**
- IAM Policies - which API calls should be allowed for a specific user from IAM

**Resource-Based**
- Bucket Policies - bucket wide rules from the S3 console - allows cross account
- Object Access Control List (ACL) - finer grain control (can be disabled)
- Bucket Access Control List (ACL) - less common (can be disabled)

An IAM Principal can access an S3 object if:
- The user IAM Permissions ALLOW it OR the resource policy ALLOWs it
- There is no explicit DENY

Another way to do security on S3 is to encrypt the objects using encryption keys.

# S3 Bucket Policies

Policy structure:
- **Resources**: buckets and objects
- **Effect**: Allow / Deny
- **Actions**: Set of API to Allow or Deny
- **Principal**: The account or user to apply the policy to

Use S3 bucket for policy to:
- Grant public access to the bucket
- Force objects to be encrypted at upload
- Grant access to another account (Cross account)


![[Pasted image 20240108153305.png]]
This policy allows anyone to read from the `examplebucket`

User access to S3 buckets can also be controlled with IAM permissions. By adding a policy which grants access to a specific bucket, the user will be able access it.

**EC2 instance access - Use IAM Roles**

EC2 instance acess can also be configured using IAM. The correct way to do this is to create a **EC2 instance role** and assign the correct IAM permissions.

**Cross-Account Access - Use Bucket Policy**

If we want to allow cross-account acces, then we must use a bucket policy

Another thing that we have to be aware of when talking about S3 security is **Bucket settings for blocking public access**.

![[Pasted image 20240108154649.png]]

These settings were created by AWS to prevent company data leaks. Therefore, **if you know your bucket should never be public, leave these on**.