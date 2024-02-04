CloudFormation is a declarative way of outlining your AWS infrastructure. It will create resources you want in the right order, with the exact configuration that you specify.

Benefits of CloudFormation:
- Infrastructure as Code
	- No resource is manually created, great for control
	- The code can be version control using git
	- Changes to the infrastructure are reviewed through PRs
- Cost
	- Each resource is tagged so you can easily see how much it costs
	- You can estimate the costs of your resources using the CloudFormation template
	- Advanced saving strategies; ex. Delete dev environment during outside of business hours and then recreate it in the morning
- Productivity
	- destroy and re-create infrastructure on the fly
	- Automated generation of diagrams
	- Declarative programming
- Separation of concerns
	- Ability to create many stack for different uses (ex. VPC stack, network stack, app stacks)

Templates are uploaded to S3 in the background and then referenced in CloudFormation. To update a template, we have to upload a new version to AWS.

Stacks are identified by name and deleting a stack deletes every single artifact with it.

### Deploying templates

**Manual way**:
- Editing templates in the CloudFormation Designer
- Using the AWS console to input and manage parameters, deploy...

Automated Way:
- Editing templates in YAML file
- Using the AWS CLI to deploy templates
- This is the recommeded way when you want to automate your flow

# Stack Policies

By default, all update actions are allowed during CloudFront stack updates. A stack policy is a JSON document that defines the update actions that are allowed on specific resources during Stack updates.

When you specify a Stack policy, all resources in the stack are protected and we need to specify explicit ALLOW for the resources you want to be allowed to be updated

![[Pasted image 20240204221137.png]]
Example: Allow updates on all resources except the production database