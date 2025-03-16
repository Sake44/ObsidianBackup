**Vertical Scaling**
 
**Increase the instance size.** ==If too many requests are sent to a single active-passive system, the active server will become unavailable and, hopefully, fail over to the passive server. But this doesn’t solve anything.==
 
==With active-passive systems, you need vertical scaling. This means increasing the size of the server. With EC2 instances, you select either a larger type or a different instance type. This can be done only while the instance is in a stopped state. In this scenario, the following steps occur:==

1. **Stop the passive instance.** ==This doesn’t impact the application because it’s not taking any traffic.==
2. **Change the instance size or type,** ==and then start the instance again.==
3. **Shift the traffic** ==to the passive instance, turning it active.==
4. **Stop, change the size, and start** ==the previous active instance because both instances should match.==

==When the number of requests reduces, you must do the same operation. Even though there aren’t that many steps involved, it’s actually a lot of manual work. Another disadvantage is that a server can only scale vertically up to a certain limit.==

**Horizontal** **Scaling**
 
**Add additional instances.** As mentioned, for the application to work in an active-active system, it’s already created as stateless, not storing any client sessions on the server. This means that having two or four servers wouldn’t require any application changes. It would only be a matter of creating more instances when required and shutting them down when traffic decreases. The Amazon EC2 Auto Scaling service can take care of that task by automatically creating and removing EC2 instances based on metrics from Amazon CloudWatch.

**Amazon EC2 Auto Scaling features**  
The Amazon EC2 Auto Scaling service adds and removes capacity to keep a steady and predictable performance at the lowest possible cost.

You can use a launch template to manually launch an EC2 instance or for use with Amazon EC2 Auto Scaling. It also supports versioning, which can be used for quickly rolling back if there's an issue or a need to specify a default version of the template.
 ![Example of a launch template with three versions. Refer to the caption for details.](Exported%20image%2020250315115744-0.png)  

Simple Scaling Group
 
With a simple scaling policy, you can do exactly what’s described in this module. You use a CloudWatch alarm and specify what to do when it is invoked. This can include adding or removing a number of EC2 instances or specifying a number of instances to set the desired capacity to. You can specify a percentage of the group instead of using a number of EC2 instances, which makes the group grow or shrink more quickly.
 
After the scaling policy is invoked, it enters a cooldown period before taking any other action. This is important because it takes time for the EC2 instances to start, and the CloudWatch alarm might still be invoked while the EC2 instance is booting
 
Step Scaling Group  
Step scaling policies respond to additional alarms even when a scaling activity or health check replacement is in progress. Similar to the previous example, you might decide to add two more instances when CPU utilization is at 85 percent and four more instances when it’s at 95 percent.
 
**Target Tracking Scaling Policy**  
If your application scales based on average CPU utilization, average network utilization (in or out), or request count, then this scaling policy type is the one to use. All you need to provide is the target value to track, and it automatically creates the required CloudWatch alarms.

**Resources**  
For more information, see the following resources:

- AWS website: [Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/)
- AWS website: [Amazon EC2 Auto Scaling FAQs](https://aws.amazon.com/ec2/autoscaling/faqs/)
- AWS user guide: [Set capacity limits on your Auto Scaling group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/asg-capacity-limits.html)
- AWS user guide: [Step and simple scaling policies for Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html)
- AWS user guide: [Target tracking scaling policies for Amazon EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html)
- AWS user guide: [Create an Auto Scaling group using a launch template](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-launch-template.html)