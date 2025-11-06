A container is a standardized unit that packages your code and its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment.

#### Difference between VMs and Containers
Containers share the same operating system and kernel as the host that they exist on. But virtual machines contain their own operating system. Each virtual machine must maintain a copy of an operating system, which results in a degree of wasted resources.

![[Pasted image 20251026153710.png]]

A container is more lightweight. Containers spin up quicker, almost instantly. Container can provide speed. 

### Amazon ECS
Amazon ECS is an end-to-end container orchestration service that helps you spin up new containers. With Amazon ECS, your containers are defined in a task definition that you use to run an individual task or a task within a service. You have the option to run your tasks and services on a serverless infrastructure that's managed by another AWS service called AWS Fargate. 

![[Pasted image 20251026153827.png]]
Amazon ECS works by helping you run Docker containers across a managed cluster of Amazon Elastic Compute Cloud (Amazon EC2) instances or in a serverless environment using AWS Fargate.
Amazon ECS is deeply integrated with other AWS Services such as, IAM, ELB. 

To prepare your application to run on Amazon ECS, you create a task definition. The task definition is a text file, in JSON format, that describes one or more containers. A task definition is similar to a blueprint that describes the resources that you need to run a container.
A deeper knowledge on ECS can be achieved at: [[AWS Elastic Container Service (ECS)]]

#### Amazon ECS core functionality
Amazon ECS provides a robust platform for running containerized workloads in the AWS Cloud. The service manages the underlying infrastructure needed to run containers at scale.
##### Container Orchestration
Container orchestration is the fundamental capability of Amazon ECS, which you can use to define how your containerized applications should run. You can specify CPU and memory requirements, networking configurations and so on.
##### Cluster management
Amazon ECS manages the infrastructure that hosts your containers, whether you choose EC2 instances or serverless Fargate. The service organizes your compute resources into logical groupings called clusters.
##### Application lifecycle management
Amazon ECS provides tools and capabilities to manage the entire lifecycle of your containerized applications. This includes deployment, scaling, updates, and termination of your containers.
The service supports various deployment strategies such as rolling updates, blue/green deployments (through AWS CodeDeploy integration), and canary deployments
#### Amazon ECS technical concepts
##### Container
Containers are lightweight, standalone executable packages that include everything you need to run a piece of software. They contain the application code, runtime, system tools, libraries, and settings.
##### Task Definitions
Task definitions are JSON files that describe one or more containers that form your application. They function as the blueprint for your application deployment on Amazon ECS.

In a task definition, you specify parameters for each container. These include Docker images, CPU and memory allocation, port mappings and so on.
##### Tasks
Tasks are the instantiation of a task definition within an Amazon ECS cluster. A task represents a running set of containers deployed together as defined in your task definition.

Tasks are the basic unit of deployment in Amazon ECS. When you run a standalone task or create a service, you're launching tasks based on your task definition.
##### Services
The Amazon ECS service scheduler launches a new task instance if one fails or stops to make sure the desired task count is maintained. An Amazon ECS service maintains a specified number of task instances running simultaneously.
##### Clusters
A cluster is a logical grouping of tasks or services. It represents the pool of compute resources available for your containerized applications.
##### Launch types
Amazon ECS provides two launch types that determine the underlying infrastructure where your containers run: EC2 launch types and Fargate launch types.

With the EC2 launch type, you manage a cluster of EC2 instances that host your containers.
With the Fargate launch type, AWS manages the underlying infrastructure. You pay only for the resources used by your containers
##### Container agent
The Amazon ECS container agent runs on each container instance in your cluster. It handles communication between your container instances and the Amazon ECS service.

The agent communicates instance task status and resource usage to Amazon ECS, while initiating or terminating tasks as directed by the Amazon ECS service.
##### Capacity providers
Capacity providers are used to manage the infrastructure for your Amazon ECS tasks. You can use capacity providers to define a strategy for how your tasks use different infrastructure options.
##### Task placement strategies
Amazon ECS employs task placement strategies to decide where to position tasks in your cluster and which ones to terminate during scale-in events.

Amazon ECS supports several placement strategies, including bin pack, random, and spread. 
- The bin pack strategy refers to placing tasks on as few instances as possible to minimize costs.
- The random strategy places tasks randomly across the cluster. 
- The spread strategy distributes tasks evenly across instances based on a specified value.
#### Amazon ECS practical business applications
##### Microservices architecture
Organizations use Amazon ECS to implement microservices architectures by deploying each service as a separate container or set of containers. Using this approach, teams can develop, deploy, and scale components independently.
##### Batch processing
Organizations use Amazon ECS for batch processing workloads that need to process large volumes of data efficiently. The service's ability to quickly scale up to handle processing demands and then scale down when complete helps optimize costs.
##### Web applications and APIs
Companies deploy web applications and APIs on Amazon ECS to benefit from its scalability and integration with Application Load Balancer. This combination provides a robust platform for handling variable traffic loads.

You can configure Amazon ECS services to automatically scale based on demand to ensure your web application remains responsive during traffic spikes.
##### Machine Learning workflows
Data science teams use Amazon ECS to containerize and orchestrate machine learning (ML) workflows, from data preprocessing to model training and deployment. Containers provide consistency across development and production environments.

With Amazon ECS, data scientists can package their entire ML environment, including frameworks like TensorFlow or PyTorch, into containers

Amazon ECS supports running batch jobs through the RunTask API or by integrating with AWS Batch for more complex job scheduling and dependencies.
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