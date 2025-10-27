### Use metrics to solve problems
The AWS resources that host your solutions create various forms of data that you might be interested in collecting. Each individual data point that a resource creates is a metric. Metrics that are collected and analyzed over time become statistics, such as average CPU utilization over time showing a spike.

### Monitoring benefits
 
**Respond proactively**
 
**Respond to operational issues proactively before your end users are aware of them.** Waiting for end users to let you know when your application is experiencing an outage is a bad practice. Through monitoring, you can keep tabs on metrics like error response rate and request latency.
 
**Improve performance and reliability**
 
**Monitoring can improve the performance and reliability of your resources.** Monitoring the various resources that comprise your application provides you with a full picture of how your solution behaves as a system. Monitoring, if done well, can illuminate bottlenecks and inefficient architectures. This helps you drive performance and improve reliability.
 
**Recognize security threats and events**
 
**By monitoring, you can recognize security threats and events.** When you monitor resources, events, and systems over time, you create what is called a baseline. A baseline defines normal activity.

**Make data-driven decisions**
**Monitoring helps you make data-driven decisions for your business.** Monitoring keeps an eye on IT operational health and drives business decisions.

**Create cost-effective solutions**
**Through monitoring, you can create more cost-effective solutions.** You can view resources that are underused and rightsize your resources to your usage. This helps you optimize cost and make sure you aren’t spending more money than necessary.
### Amazon CloudWatch
Amazon CloudWatch is a monitoring and observability service that collects your resource data and provides actionable insights into your applications.
 With CloudWatch, you can respond to system-wide performance changes, optimize resource usage, and get a unified view of operational health.
### Visibility using CloudWatch
AWS resources create data that you can monitor through metrics, logs, network traffic, events, and more. This data comes from components that are distributed in nature.
 
You can use CloudWatch to do the following:
 
•Detect anomalous behavior in your environments.  
•Set alarms to alert you when something is not right.  
•Visualize logs and metrics with the AWS Management Console.  
•Take automated actions like scaling.  
•Troubleshoot issues.  
•Discover insights to keep your applications healthy.

Many AWS services automatically send metrics to CloudWatch for free at a rate of 1 data point per metric per 5-minute interval. This is called basic monitoring, and it gives you visibility into your systems without any extra cost. For many applications, basic monitoring is adequate.
 
For applications running on EC2 instances, you can get more granularity by posting metrics every minute instead of every 5-minutes using a feature like detailed monitoring.

### CloudWatch concepts
Metrics are the fundamental concept in CloudWatch. A metric represents a time-ordered set of data points that are published to CloudWatch. Think of a metric as a variable to monitor and the data points as representing the values of that variable over time.

### CloudWatch dashboards
Once you provision your AWS resources and they are sending metrics to CloudWatch, you can visualize and review that data using CloudWatch dashboards. Dashboards are customizable home pages you can configure for data visualization for one or more metrics through widgets, such as a graph or text.
 
You can build many custom dashboards, each one focusing on a distinct view of your environment. You can even pull data from different AWS Regions into a single dashboard to create a global view of your architecture.

An alarm can be invoked when it transitions from one state to another. After an alarm is invoked, it can initiate an action. Actions can be an Amazon EC2 action, an automatic scaling action, or a notification sent to Amazon Simple Notification Service (Amazon SNS).

### Amazon CloudWatch Logs
CloudWatch Logs is centralized place for logs to be stored and analyzed. With this service, you can monitor, store, and access your log files from applications running on EC2 instances, AWS Lambda functions, and other sources. With CloudWatch Logs, you can query and filter your log data.
An alarm can be invoked when it transitions from one state to another. After an alarm is invoked, it can initiate an action.
### CloudWatch Alarms
You can create CloudWatch alarms to automatically initiate actions based on sustained state changes of your metrics. You configure when alarms are invoked and the action that is performed.

First, you must decide which metric you want to set up an alarm for, and then you define the threshold that will invoke the alarm. Next, you define the threshold's time period.
CloudWatch Alarms can have three states of an alarm: 
1. OK
2. ALARM
3. INSUFFICIENT_DATA

### Resources 
For more information, see the following resources:

- AWS website: [Amazon CloudWatch Pricing](https://aws.amazon.com/cloudwatch/pricing/)
- AWS website: [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)
- AWS user guide: [Getting Started with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/GettingStarted.html)
- AWS user guide: [What Is Amazon CloudWatch Logs?](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)
- AWS user guide: [AWS services that publish CloudWatch metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/aws-services-cloudwatch-metrics.html)
- AWS user guide: [View available metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/viewing_metrics_with_cloudwatch.html)
- AWS website: [Amazon SNS](https://aws.amazon.com/sns/)
- AWS user guide: [Best practices for monitoring](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_best_practices.html)
- AWS website: [Monitoring and Observability](https://aws.amazon.com/cloudops/monitoring-and-observability/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc&blog-posts-cards.sort-by=item.additionalFields.createdDate&blog-posts-cards.sort-order=desc)
- AWS user guide: [Monitor Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_ec2.html)
- AWS user guide: [Monitoring Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/monitoring-overview.html)
- AWS user guide: [Monitoring metrics in an Amazon RDS instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Monitoring.html)