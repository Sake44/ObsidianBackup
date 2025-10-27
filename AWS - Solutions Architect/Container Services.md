A container is a standardized unit that packages your code and its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment.

#### Difference between VMs and Containers
Containers share the same operating system and kernel as the host that they exist on. But virtual machines contain their own operating system. Each virtual machine must maintain a copy of an operating system, which results in a degree of wasted resources.

![[Pasted image 20251026153710.png]]

A container is more lightweight. Containers spin up quicker, almost instantly. Container can provide speed. 

### Amazon ECS

Amazon ECS is an end-to-end container orchestration service that helps you spin up new containers. With Amazon ECS, your containers are defined in a task definition that you use to run an individual task or a task within a service. You have the option to run your tasks and services on a serverless infrastructure that's managed by another AWS service called AWS Fargate. 

![[Pasted image 20251026153827.png]]
To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers. A task definition is similar to a blueprint that describes the resources that you need to run a container.

### Amazon EKS
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services. By bringing software development and operations together by design, Kubernetes created a rapidly growing ecosystem that is very popular and well established in the market.
 
Amazon EKS is conceptually similar to Amazon ECS, but with the following differences:  
1. In Amazon ECS, the machine that runs the containers is an EC2 instance that has an ECS agent installed and configured to run and manage your containers. This instance is called a container instance. In Amazon EKS, the machine that runs the containers is called a worker node or Kubernetes node.
2. An ECS container is called a task. An EKS container is called a pod.
3. Amazon ECS runs on AWS native technology. Amazon EKS runs on Kubernetes.

### Resources ECS and EKS
- AWS website: [Containers on AWS(opens in a new tab)](https://aws.amazon.com/containers/services/)
- External website: [Docker: Use Containers to Build, Share and Run Your Applications(opens in a new tab)](https://www.docker.com/resources/what-container)
- AWS website: [Amazon Elastic Container Service (Amazon ECS)(opens in a new tab)](https://aws.amazon.com/ecs/)
- External website: [Github: Amazon ECS Agent(opens in a new tab)](https://github.com/aws/amazon-ecs-agent)
- AWS developer guide: [Amazon ECS Container Instances(opens in a new tab)](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html)
- External website: [Coursera course: Building Containerized Applications on AWS(opens in a new tab)](https://www.coursera.org/learn/containerized-apps-on-aws)
- AWS website: [Amazon Elastic Kubernetes Service (EKS)(opens in a new tab)](https://aws.amazon.com/eks/)
- AWS user guide: [Amazon EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)