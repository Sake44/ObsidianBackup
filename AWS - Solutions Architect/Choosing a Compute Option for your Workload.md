## Assessing your workload
A workload identifies a set of components that together deliver business value.
### Amazon Ec2 considerations
With Amazon EC2, you have complete control of your computing resources. Amazon EC2 reduces the time required to obtain and start new server instances to minutes.
Because EC2 instances are virtualized servers in the cloud, they lend themselves to support a large variety of applications. Anything you can run on a physical server can be run on Amazon EC2.

When you have compute-intensive or memory-intensive applications, consider the following:
- You can select a specific instance type based on the requirements of the application or software that you plan to run on your instance. 
- Amazon EC2 provides each instance with a consistent and predictable amount of CPU capacity,** regardless of its underlying hardware.
- Amazon EC2 works with other AWS services to provide a complete solution for computing, query processing, and storage across a wide range of applications.
	- - From a performance perspective, **you can use i****nstances for long-running, stateful applications.**
	- **You can determine the type and size or your storage,** whether to use block or file storage.
- Ec2 Instances are optimized for use cases
- Ec2 is versatile and reliable. You can run a simple website or you can run a vast, complex, custom-built application, and when necessary, replacement instances can be rapidly and predictably deployed.
### Considerations for containers

We can consider to use container for:
- For compute-intensive workloads
	- Applications that are compute intensive run better in a container environment.
- For large monolithic applications
	- You can break apart applications and run them as independent components, called **microservices, using containers to isolate processes**.
		- By using microservices, you can break large applications into smaller, self-contained pieces. 
		- Segmenting a larger app
		- lication means that updates can be applied on only specific parts. Because each part of the larger application resides in its own container, an update that might have affected files used by a different piece of the application is isolated to its own container.
		- With containers, you can do **frequent updates** by pushing out new containers.
- When you need to scale quickly
	- Containers can be built and taken down quickly.
- When you need to move your large application to the cloud without altering the code
	- With containers, you can package entire applications and move them to the cloud without the need to make any code changes. 
	- Your application can be as large as you need it to be and can run as long as you require it to run.

When NOT to use containers: 
- When applications need persistent storage of data storage.
	- Containers can absolutely support persistent storage; however, it tends to be easier to containerize applications that don't require persistent storage.
- When container have complex networking, routing or security requirements
	- Containers are portable and can be moved through different environments (testing, staging, production). If the application requires a complex configuration for networking, routing, storage, and so on, the containers are much more challenging to move.

![[Pasted image 20251105101420.png]]

### Additional compute options
AWS offer hundreds of different compute options. We already mentioned AWS Lambda, you can read about it to this page: [[Serverless]]. 

#### AWS Step Functions
AWS Step Functions is a fully managed service that you can use to coordinate the components of distributed applications and microservices using visual workflows. You build small applications that each perform a discrete function (or step) in your workflow, which means that you can scale and change your applications quickly.
Step Functions is a reliable way to coordinate components and step through the functions of your application. Step Functions provides a graphical console to arrange and visualize the components of your application as a series of steps
#### AWS Batch
Batch computing is defined as the running of a program without manual intervention. The program's input parameters are predefined through scripts, command-line arguments, control files, or job control language.
A given batch job might depend on the completion of preceding jobs or on the availability of certain inputs.
#### AWS Elastic Beanstalk
With Elastic Beanstalk, developers upload their application. Then, Elastic Beanstalk automatically handles the deployment details of capacity provisioning, load balancing, auto-scaling, and application health monitoring. By using Elastic Beanstalk, developers can focus on developing their application and are freed from deployment-oriented tasks.
#### Amazon Lightsail
With a virtual private server (VPS), also known as an instance, users can run websites and web applications in a highly secure and available environment. Lightsail is a VPS provider and is a useful way to get started with AWS for users who need a solution to build and host their applications on AWS Cloud.
Lightsail provides developers with compute, storage, and networking capacity and capabilities to deploy and manage websites and web applications in the cloud. Lightsail includes everything you need to launch your project quickly for a low, predictable monthly price. This includes VMs, containers, databases, content delivery network (CDN), load balancers, Domain Name System (DNS) management, and so on.

**So what is the difference between Amazon EC2 and Lightsail?** Lightsail provides low-cost, pre-configured cloud resources for simple workloads just starting on AWS. Amazon EC2 is a compute web service that provides secure, resizable compute in the cloud. It has far greater scale and optimization capabilities than Lightsail.

[Amazon Lightsail or Amazon EC2 (Compare Free Cloud Servers)](https://aws.amazon.com/free/compute/lightsail-vs-ec2/): A comparison of AWS Lightsail and Amazon EC2
