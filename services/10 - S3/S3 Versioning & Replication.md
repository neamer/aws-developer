# Versioning

Versioning is enabled at the **bucket level.**

Versioning your buckets is considered best-practice because:
- Protects agains unintended deletes (ability to restore a version)
- Easy roll back to previous version

Note that:
- Files that were added before we enabled versioning will have Version ID set to `null`
- Suspending versioning does not delete the previous versions

With versioning enabled we have two options for deleting objects:
- **permanently delete** - This will completely erase a single version of a object with no ability to recovered the data after
- **delete marker** - This creates a new version with the type "Delete marker". This is a soft deletion mechanism and the files can be recovered by removing the delete marker.

# Replication

Version must be enabled in both the source and destination buckets.

Depending on the region of the source and destination buckets we can have:
- Cross-Region Replication (CRR)
- Same-Region Replication (SRR)

After enabling replication, **only new objects are replicated**. To replicate existing objects we can use **S3 Batch Replication** which replicates existing objects and objects that failed replication 

Things to note:
- Buckets can be in different AWS accounts
- Copying is asynchronous
- Must give proper IAM permissions to S3
- Delete markers can be replicated (with the **Delete Market Replication** option)
- Permanent deletes are not replicated (to avoid malicious deletes)
- **There is no 'chaining' of replication** - If bucket 1 has replication into bucket 2, which has replicaiton into bucket 3. Then objects created in bucket 1 are not replicated to bucket 3

Use cases:
- CRR - compliance, lower latency access, replication across accounts
- SRR - log aggregation, live replication between production and test accounts