
**S3 User-Defined Object Metadata** are key-value pairs which we can attach to objects that begin with 'x-amz-meta-' and which can be retrieved while accessing the object.

**S3 Object Tags** are also key-value pairs for object in S3. They are useful fo fine-grained permissions (only access specific objects with specific tags) and for analytic purposes.

**You cannot search the object metadata or object tags**. To do that, you must use an external DB as a search index such as DynamoDB