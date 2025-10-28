## What does AWS Control Tower do?

If you have multiple Amazon Web Services (AWS) accounts and teams, cloud setup and governance can be complex and time consuming. It might slow down the very innovation that you’re trying to speed up. AWS Control Tower provides a straightforward way to set up and govern a secure, multi-account AWS environment, called a landing zone. It uses AWS Organizations to create your landing zone.
## AWS Control Tower core functionality
AWS Control Tower delivers three primary functions that work together to help you govern your AWS environment at scale.
### Landing zone setup
AWS Control Tower automates the creation of a well-architected multi-account environment based on AWS best practices. This landing zone includes a logically separated organizational structure with dedicated accounts for management, log archive, and audit purposes.
### Guardrails implementation
Guardrails are high-level rules that provide ongoing governance for your AWS environment. They help you implement compliance requirements by preventing deployment of resources that don't conform to your policies.

AWS Control Tower offers two types of guardrails. Preventive guardrails use service control policies (SCPs) to stop actions before they occur. Detective guardrails use AWS Config rules to identify non-compliant resources after they are created.
### Account Factory provisioning
Account Factory provides a standardized, automated way to provision and configure new AWS accounts that conform to your organization's compliance requirements.
Account Factory integrates with AWS Service Catalog to create a repeatable process for account creation.

**What problems does AWS Control Tower solve?**  
AWS Control Tower provides mandatory and strongly recommended high-level rules, called guardrails. These help enforce your policies using service control policies (SCPs) or detect policy violations using AWS Config rules.
 ![Exported image](Exported%20image%2020250315115752-0.png)
## AWS Control Tower Technical Concept
AWS Control Tower operates across multiple IT domains, including cloud governance, identity management, security, and compliance.
### Organizations and Organizational units
Organizations in AWS Control Tower represent the hierarchical structure of your accounts. An organization is the root container for all your AWS accounts, and organizational units (OUs) are logical groupings of accounts within that structure.
### Landing Zone
A landing zone is a well-architected, multi-account AWS environment that follows best practices for security and compliance. It serves as the foundation for your cloud adoption journey.
### Guardrails
Guardrails are governance rules that help you maintain control over your AWS environment. They implement specific governance, compliance, or security requirements across multiple accounts.
### Account Factory
Account Factory is a standardized account-provisioning service that helps you create new AWS accounts that comply with your organization's standards. It provides a repeatable blueprint for account creation.
### Drift detection
Drift occurs when resources in your AWS Control Tower environment are modified outside of the AWS Control Tower governance. Drift detection identifies these changes that might compromise your governance model.
### Share responsibility model
The AWS Shared Responsibility Model defines the security responsibilities between AWS and customers.
### Baseline Configuration
Baseline configuration represents the standard settings and services deployed to each account in your AWS Control Tower environment. It establishes a consistent starting point for all accounts.
### Compliance Framework
Guardrails in AWS Control Tower can be mapped to requirements from framework, such as the following:
- National Institute of Standards and Technology (NIST)
- Payment Card Industry Data Security Standard (PCI DSS)
- Health Insurance Portability and Accountability Act of 1996 (HIPAA)
## What are the benefits of AWS Control Tower? 
Distributed teams can provision new AWS accounts quickly, while cloud IT has the peace of mind of knowing that all accounts align with centrally established, company-wide policies. AWS Control Tower provides a single location to set up your new well-architected, multi-account environment and govern your AWS workloads with rules for security, operations, and internal compliance. 

![AWS Control Tower architecture diagram. Details are discussed in the following interactive markers and text that follows.](Exported%20image%2020250315115752-1.png)  

**What does AWS Control Tower do automatically?**  
As part of this framework, AWS Control Tower automatically does the following:
 
- Turns on CloudTrail and AWS Config and facilitates centralized login to an Amazon S3 bucket, which is located in a log archive account - Preconfigures Amazon SNS topics that other services can subscribe to - Provides federated access to accounts using IAM Identity Center - Turns on guardrails to protect the resources that AWS Control Tower deploys and detects non-compliance across multiple accounts - Supports lifecycle events so that you can configure any additional custom automations as part of new account creation