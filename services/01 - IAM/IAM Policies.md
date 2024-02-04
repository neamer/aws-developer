A **policy** is a JSON document which is used to define permissions.

Policies can be ascribed to users or groups.

When applying policies, we should use the [[Least privilege principle]].

Policies can be divided into three categories:

- **AWS managed policies** - An _AWS managed policy_ is a standalone policy that is created and administered by AWS.
- **Customer managed policies** - You can create standalone policies in your own AWS account that you can attach to principal entities (users, groups, and roles). You create these _customer managed policies_ for your specific use cases, and you can change and update them as often as you like.
- **Inline policies** - An inline policy is a policy created for a single IAM identity (a user, group, or role). Inline policies maintain a strict one-to-one relationship between a policy and an identity. They are deleted when you delete the identity.

#### IAM Policy inheritance 



#### [[IAM Policy Structure]]

