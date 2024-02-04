S3 Lifecycle rules allow us to automate moving objects betweem [[S3 Storage Classes]]

These lifecycle rules are made out of:
- **Transition Actions** - transfer objects to another storage class after a certain amount of time
- **Expiration Actions** - configure objects to expire (delete) after some time
	- Can be used to delete old versions of files (if versioning is enabled)
	- Can be used to delete incomplete Multi-Part uploads

Rules can be created for a certain prefix (example: s3://mybucket/mp3/*)

Rules can also be created for certain object [[Tags]] (example: Department: Finance)

# Examples

### Example 1

![[Pasted image 20240117161610.png]]

The solution here is to:
- Use the **Standard** storage class for the source images, with a lifecycle rule to transition to **Glacier** after 60 days.
- Use **One-Zone IA**, with a lifecycle configuration to expire (delete) them after 60 days.


### Example 2

![[Pasted image 20240117161826.png]]

The solution there is to:
- Enable S3 Versioning make the delete functionality use delete markers instead of permanent deletion
- Transition the non-current versions of objects to **Standard IA** after 30 days using lifecycle configuration
- Transition the non-current versions of objects to **Glacier Deep Archive** after 365 days using lifecycle configuration