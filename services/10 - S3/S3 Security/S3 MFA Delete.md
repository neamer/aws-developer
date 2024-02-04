MFA Delete is an extra protection mechanism that forces users to generate a code on a device (usually a mobile phone or hardware) before doing important operations on S3

MFA will be required to:
- Permanently delete an object version
- Suspend versioning on the bucket

MFA won't be required to:
- Enable versioning
- List deleted versions

To use MFA Delete, **Versioning must be enabled** on the bucket

**Only the bucket owner (root account) can enable/disable MFA Delete**