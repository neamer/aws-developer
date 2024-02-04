This feature has a different name depending on the generation of the load balander used:
- Connection draining - for CLB
- Deregistration Delay - for ALB & NLB


When Connection Draining is enabled and configured, the process of deregistering an instance from an Elastic Load Balancer gains an additional step. For the duration of the configured timeout, the load balancer will allow existing, in-flight requests made to an instance to complete, but it will not send any new requests to the instance.

Once the timeout is reached, any remaining connections will be forcibly closed.