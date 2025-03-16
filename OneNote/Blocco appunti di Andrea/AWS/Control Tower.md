**What does AWS Control Tower do?**  
If you have multiple Amazon Web Services (AWS) accounts and teams, cloud setup and governance can be complex and time consuming. It might slow down the very innovation that you’re trying to speed up. AWS Control Tower provides a straightforward way to set up and govern a secure, multi-account AWS environment, called a landing zone. It uses AWS Organizations to create your landing zone.
   

**What problems does AWS Control Tower solve?**  
AWS Control Tower provides mandatory and strongly recommended high-level rules, called guardrails. These help enforce your policies using service control policies (SCPs) or detect policy violations using AWS Config rules.
 ![Exported image](Exported%20image%2020250315115752-0.png)  

**What are the benefits of AWS Control Tower?**  
Distributed teams can provision new AWS accounts quickly, while cloud IT has the peace of mind of knowing that all accounts align with centrally established, company-wide policies. AWS Control Tower provides a single location to set up your new well-architected, multi-account environment and govern your AWS workloads with rules for security, operations, and internal compliance. 

![AWS Control Tower architecture diagram. Details are discussed in the following interactive markers and text that follows.](Exported%20image%2020250315115752-1.png)  

**What does AWS Control Tower do automatically?**  
As part of this framework, AWS Control Tower automatically does the following:
 
- Turns on CloudTrail and AWS Config and facilitates centralized login to an Amazon S3 bucket, which is located in a log archive account - Preconfigures Amazon SNS topics that other services can subscribe to - Provides federated access to accounts using IAM Identity Center - Turns on guardrails to protect the resources that AWS Control Tower deploys and detects non-compliance across multiple accounts - Supports lifecycle events so that you can configure any additional custom automations as part of new account creation
      

**What types of guardrails does AWS Control Tower provide?**  
AWS Control Tower provides two types of guardrails: 
 
**Preventive guardrails** prevent policy violations through enforcement and are implemented using AWS CloudFormation and SCPs.
 
**Detective guardrails** detect policy violations and alert in the dashboard. Detective controls are implemented by using AWS Config rules.