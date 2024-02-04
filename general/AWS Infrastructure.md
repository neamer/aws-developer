An **AWS Region** is a physical location where data centers are clustered.

An **Availability Zone (AZ)** is one or more discrete data centers with redundant power, networking, and connectivity in an AWS Region. A region has at least three and at most six AZ's. They are separate from each other so that they are isolated from disasters.

Relevant factors when choosing AWS Regions for our use-cases:

* **Compliance with data governance and legal requirements.** Data never leaves a region without explicit permission.
* **Proximity to customers.** Reduced latency.
* **Available Services.** New features and services aren't available in every region.
* **Pricing** varies from region to region.

In addition to the AWS Regions and Availability Zones, AWS also operates a globally distributed **Point of presence (PoP)** network.

While some services are considered Global, most of them are Region-specific. To check service availability by region we can use the [AWS Regional Services site](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/).