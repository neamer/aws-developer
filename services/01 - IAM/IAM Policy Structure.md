IAM Policies consist of:
- **Version** - Policy language version (not the version of the actual policy itself)
- **Id** - Identifier for the policy (optional)
- **Statement** - One or more individual statements

The statements consist of:
- **Sid** - An identifier for the statement (optional)
- **Effect** - Whether the statement allows or denies access
- **Principal** - account/user/role to which this policy applies to
- **Actions** - List of actions this policy allows or denies
- **Resource** - List of resources to which the actions applies to
- **Condition** - Conditions for when the policy is in effect (optional)

Multiple actions and resources can be selected via the * wildcard