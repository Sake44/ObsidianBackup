Amazon GuardDuty is a threat detection service that continuously monitors your AWS accounts, workloads, and data for malicious activity. With GuardDuty, you can use machine learning, anomaly detection, and integrated threat intelligence to identify unexpected and potentially unauthorized activity within your AWS environment.
GuardDuty helps detect various threat scenarios in your AWS environment. These include compromised AWS credentials, data exfiltration attempts, and unusual login patterns
## GuardDuty core functionality
GuardDuty automatically ingests and analyzes foundational data sources including AWS CloudTrail management events, Amazon Virtual Private Cloud (Amazon VPC) Flow Logs, and VPC DNS logs.
This capability identifies multi-stage attacks that span across different data sources, AWS resources, and time periods within an AWS account.
GuardDuty offers specialized protection plans for specific AWS services and resources:

- **S3 Protection** monitors data access patterns
- **Amazon EKS Protection** analyzes Kubernetes audit logs
- **Runtime Monitoring** detects threats at the OS level in EC2 instances, Amazon EKS clusters, and ECS container workloads
- **Malware Protection** scans EC2 instances and S3 objects
- **Amazon RDS Protection** monitors database login activity
- **AWS Lambda Protection**nitors function network activity
## Amazon GuardDuty technical concepts
The detector is the foundational component of GuardDuty that manages threat detection in each AWS region.
GuardDuty processes multiple data sources to provide comprehensive visibility into your AWS environment.
GuardDuty uses both AWS managed threat intelligence feeds and custom threat lists that you can configure.
Sophisticated machine learning algorithms analyze patterns of activity to establish baselines of normal behavior.
When GuardDuty detects suspicious activity, it generates findings with detailed information about the potential threat.
GuardDuty supports management across multiple accounts using AWS Organizations.
## Amazon GuardDuty architecture
Amazon GuardDuty employs a comprehensive architecture that helps with threat detection across your AWS environment without requiring complex setup or management.
![[Pasted image 20251030121352.png]]
### Integration considerations
Use AWS Identity and Access Management (IAM) roles and policies to manage service access to Amazon GuardDuty, implement encryption for sensitive data, and follow security best practices for authentication.
Design integrations with Amazon GuardDuty to handle varying workloads by implementing proper error handling and retry mechanisms.
Set up comprehensive monitoring for Amazon GuardDuty using Amazon CloudWatch metrics and create appropriate alarms to detect potential issues early.