![Exported image](Exported%20image%2020250315115715-0.png)

Containers share the same operating system and kernel as the host that they exist on. But virtual machines contain their own operating system. Each virtual machine must maintain a copy of an operating system, which results in a degree of wasted resources.
 
A container is more lightweight. Containers spin up quicker, almost instantly. This difference in startup time becomes instrumental when designing applications that must scale quickly during I/O bursts.

**Amazon ECS**  
==Amazon Elastic Container Service (Amazon ECS)==
   

Amazon ECS is an end-to-end container orchestration service that helps you spin up new containers. With Amazon ECS, your containers are defined in a task definition that you use to run an individual task or a task within a service. You have the option to run your tasks and services on a serverless infrastructure that's managed by another AWS service called AWS Fargate. Alternatively, for more control over your infrastructure, you can run your tasks and services on a cluster of EC2 instances that you manage.
 ![Your containers are defined in a task definition that you use to run an individual task or task within a service.](Exported%20image%2020250315115716-1.png)  

==When the Amazon ECS container instances are up and running, you can perform actions that include, but are not limited to, the following:==

- ==Launching and stopping containers==
- ==Getting cluster state==
- ==Scaling in and out==
- ==Scheduling the placement of containers across your cluster==
- ==Assigning permissions==
- ==Meeting availability requirements==
 
**Amazon EKS**  
==Amazon Elastic Kubernetes Service (EKS)==
 
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services. By bringing software development and operations together by design, Kubernetes created a rapidly growing ecosystem that is very popular and well established in the market.
 
Amazon EKS is conceptually similar to Amazon ECS, but with the following differences:  
￼1. In Amazon ECS, the machine that runs the containers is an EC2 instance that has an ECS agent installed and configured to run and manage your containers. This instance is called a container instance. In Amazon EKS, the machine that runs the containers is called a worker node or Kubernetes node. ￼2. An ECS container is called a task. An EKS container is called a pod.￼3. Amazon ECS runs on AWS native technology. Amazon EKS runs on Kubernetes.