
### Load balancer migration

After creating a EB environment, you cannot change the ELB type

To migrate to a different ELB we need to:
1. Create a new environment with the same configuration except the ELB (we cannot use the clone feature because it copies all configuration)
2. deploy your application onto the new environment
3. perform a CNAME swap or Route 53 update

### Migrating to a decoupled RDS setup

RDS can be provisioned with Beanstalk, but the RDS lifecycle will be tied to the Beanstalk environment lifecycle. This can be good for lower environments, but the best approach for prod would be to separate the RDS database and provide our EB application with the connection string.

To migrate to a setup with a decoupled DB we need to:
1. Create a snapshot of the RDS DB (as a safeguard)
2. Protect the DB from deletion with the RDS console
3. Create a new beanstalk environment without RDS, pointing our application to the existing DB
4. Perform a CNAME swap (blue/green) or Route 53 update to confirm that it is working
5. Terminate the old environment (the DB won't be deleted because of the deletion protection feature)
6. CloudFormation stack will be in the DELETE_FAILED state because of the DB so we will need to manually delete it.