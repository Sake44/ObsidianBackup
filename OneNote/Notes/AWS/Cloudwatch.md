**Visibility using CloudWatch**  
AWS resources create data that you can monitor through metrics, logs, network traffic, events, and more. This data comes from components that are distributed in nature.
 
CloudWatch is a monitoring and observability service that collects your resource data and provides actionable insights into your applications. With CloudWatch, you can respond to system-wide performance changes, optimize resource usage, and get a unified view of operational health.

==You can use CloudWatch to do the following:==
 
•Detect anomalous behavior in your environments.  
•Set alarms to alert you when something is not right.  
•Visualize logs and metrics with the AWS Management Console.  
•Take automated actions like scaling.  
•Troubleshoot issues.  
•Discover insights to keep your applications healthy.

Many AWS services automatically send metrics to CloudWatch for free at a rate of 1 data point per metric per 5-minute interval. This is called basic monitoring, and it gives you visibility into your systems without any extra cost. For many applications, basic monitoring is adequate.
 
For applications running on EC2 instances, you can get more granularity by posting metrics every minute instead of every 5-minutes using a feature like detailed monitoring.

**CloudWatch concepts**  
Metrics are the fundamental concept in CloudWatch. A metric represents a time-ordered set of data points that are published to CloudWatch. Think of a metric as a variable to monitor and the data points as representing the values of that variable over time.

**CloudWatch dashboards**  
Once you provision your AWS resources and they are sending metrics to CloudWatch, you can visualize and review that data using CloudWatch dashboards. Dashboards are customizable home pages you can configure for data visualization for one or more metrics through widgets, such as a graph or text.
 
You can build many custom dashboards, each one focusing on a distinct view of your environment. You can even pull data from different AWS Regions into a single dashboard to create a global view of your architecture.

An alarm can be invoked when it transitions from one state to another. After an alarm is invoked, it can initiate an action. Actions can be an Amazon EC2 action, an automatic scaling action, or a notification sent to Amazon Simple Notification Service (Amazon SNS).
 > From <[https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1737550800/zbwY7uARmEZo7gmWH1IkQQ/tincan/1795780_1724170242_o_1i5o8dfb5ei1rfm2uc19inhd6b_zip/index.html?enhanced_signature=KxjUSFVsbzpa4YYtq2yRCmWjwmSqJTX7e3BMn-Nv_CY&endpoint=https%3A%2F%2Fexplore.skillbuilder.aws%2Flrs-api%2F&auth=Basic%20N2E0YzJmNjUtMzBiYi00NmU4LWFiNzQtZTk5Y2YzOWNkMjk4OmFlZGQyNWYxMjZmODYyNGQxMTBlNjE2MDEwZjAwYWE5&actor=%7B%22name%22%3A%22Andrea+Rollo%22%2C%22mbox%22%3A%22mailto%3Aandrea.rollo%40capgemini.com%22%7D&registration=4b197119-ed02-47d6-83a7-f7d19c8cf9d7&activity_id=http%3A%2F%2FmAFv4fCSHfQozqnarznMmn7SUk_vcJgb_rise&Accept-Language=en&course_id=1851&content_token=4b197119-ed02-47d6-83a7-f7d19c8cf9d7&session_context=lms&host=kfase3bzbc.execute-api.us-east-1.amazonaws.com&path=/v1/xApi/&rs=6790c1be8223d&crct=2fba6dc88d7653cd83ac441f9f6d86540344f61a901613caa4fc425a89b8335433dbfe84b22a9518877134c4c410a004a389c1e1fbb482922b1c9f09d0a2cce1&course_code=TCAA-DIG-100-CETESD-0103-EN-US&course_id=1851&username=e84192e3-c78f-4598-91e8-a861f9fdd7f4&user_id=4663134&hash=20f53a7bea455c0a13abb8822431f61cb8fad8d3175f72f3170f96252eb844d5#/lessons/YLQHaXJ19Ts153R1V5LfPCiK4FmmsLsF](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1737550800/zbwY7uARmEZo7gmWH1IkQQ/tincan/1795780_1724170242_o_1i5o8dfb5ei1rfm2uc19inhd6b_zip/index.html?enhanced_signature=KxjUSFVsbzpa4YYtq2yRCmWjwmSqJTX7e3BMn-Nv_CY&endpoint=https%3A%2F%2Fexplore.skillbuilder.aws%2Flrs-api%2F&auth=Basic%20N2E0YzJmNjUtMzBiYi00NmU4LWFiNzQtZTk5Y2YzOWNkMjk4OmFlZGQyNWYxMjZmODYyNGQxMTBlNjE2MDEwZjAwYWE5&actor=%7B%22name%22%3A%22Andrea+Rollo%22%2C%22mbox%22%3A%22mailto%3Aandrea.rollo%40capgemini.com%22%7D&registration=4b197119-ed02-47d6-83a7-f7d19c8cf9d7&activity_id=http%3A%2F%2FmAFv4fCSHfQozqnarznMmn7SUk_vcJgb_rise&Accept-Language=en&course_id=1851&content_token=4b197119-ed02-47d6-83a7-f7d19c8cf9d7&session_context=lms&host=kfase3bzbc.execute-api.us-east-1.amazonaws.com&path=/v1/xApi/&rs=6790c1be8223d&crct=2fba6dc88d7653cd83ac441f9f6d86540344f61a901613caa4fc425a89b8335433dbfe84b22a9518877134c4c410a004a389c1e1fbb482922b1c9f09d0a2cce1&course_code=TCAA-DIG-100-CETESD-0103-EN-US&course_id=1851&username=e84192e3-c78f-4598-91e8-a861f9fdd7f4&user_id=4663134&hash=20f53a7bea455c0a13abb8822431f61cb8fad8d3175f72f3170f96252eb844d5#/lessons/YLQHaXJ19Ts153R1V5LfPCiK4FmmsLsF)>  

**Resources**  
For more information, see the following resources:

- AWS website: [Amazon CloudWatch Pricing](https://aws.amazon.com/cloudwatch/pricing/)
- AWS website: [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/)
- AWS user guide: [Getting Started with Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/GettingStarted.html)
- AWS user guide: [What Is Amazon CloudWatch Logs?](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)
- AWS user guide: [AWS services that publish CloudWatch metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/aws-services-cloudwatch-metrics.html)
- AWS user guide: [View available metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/viewing_metrics_with_cloudwatch.html)
- AWS website: [Amazon SNS](https://aws.amazon.com/sns/)