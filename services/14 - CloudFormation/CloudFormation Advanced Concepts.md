
### ChangeSets

Change sets allow you to preview how proposed changes to a stack might impact your running resources, for example, whether your changes will delete or replace any critical resources, AWS CloudFormation makes the changes to your stack only when you decide to execute the change set, allowing you to decide whether to proceed with your proposed changes or explore other changes by creating another change set.

An important thing to note is that change sets won't say if the update will be successful.

### Nested stacks

Nested stacks are **common components that you declare and reference from within other templates**. That way, you can avoid copying and pasting the same configurations into your templates and simplify stack updates.

Nested stacks are considered best practice in a lot of situations.

To update a nested stack, always update the parent (root stack)

### Cross vs nested stacks

Cross stacks here are referencing stacks which are based on cross-stack references for maximum reusability.

**Cross stacks**:
- Helpful when stacks have different lifecycles

![[Pasted image 20240204215818.png]]

Nested stacks:
- Helpful when components must be reused

![[Pasted image 20240204215916.png]]

### StackSets

Create, update or delete stacks across multiple accounts and regions with a single operation

Using an administrator account, you define and manage an AWS CloudFormation template, and use the template as the basis for provisioning stacks into selected target accounts across specified AWS Regions.

An administrator account is needed to create a StackSet and trusted accounts are used to create, update and delete stack instances from StackSets

![[Pasted image 20240204220204.png]]

**Anytime you see anything in the exam about updating CloudFormation stack in multiple accounts and regions, think StackSets**