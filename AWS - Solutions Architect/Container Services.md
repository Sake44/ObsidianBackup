A container is a standardized unit that packages your code and its dependencies. This package is designed to run reliably on any platform, because the container creates its own independent environment.

#### Difference between VMs and Containers
Containers share the same operating system and kernel as the host that they exist on. But virtual machines contain their own operating system. Each virtual machine must maintain a copy of an operating system, which results in a degree of wasted resources.

![[Pasted image 20251026153710.png]]

A container is more lightweight. Containers spin up quicker, almost instantly. Container can provide speed. 
Amazon EKS is conceptually similar to Amazon ECS, but with the following differences:  
1. In Amazon ECS, the machine that runs the containers is an EC2 instance that has an ECS agent installed and configured to run and manage your containers. This instance is called a container instance. In Amazon EKS, the machine that runs the containers is called a worker node or Kubernetes node.
2. An ECS container is called a task. An EKS container is called a pod.
3. Amazon ECS runs on AWS native technology. Amazon EKS runs on Kubernetes.

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
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed container orchestration service that facilitates deploying, managing, and scaling Kubernetes applications in the AWS Cloud or on premises.
#### Amazon EKS Control Plane
Amazon EKS provides a scalable, highly available control plane. Amazon EKS automatically manages the availability and scalability of the Kubernetes API servers and the etcd persistence layer for each cluster.
##### Amazon EKS availability and API
The Amazon EKS control plane consists of at least two API server nodes and three etcd nodes across three Availability Zones. Amazon EKS automatically detects and replaces unhealthy control plane nodes, which removes a significant operational burden for running Kubernetes.
![[Pasted image 20251107101930.png]]
Amazon EKS manages the Kubernetes control plane with the Amazon EKS API. You can use one of two CLIs to interact with the Amazon EKS API: Amazon EKS CLI or eksctl. With the eksctl command line utility, developed by Weaveworks, you can create and manage Kubernetes clusters on Amazon EKS. The eksctl utility uses AWS CloudFormation in the background to build clusters based on the options you specify.
#### Amazon EKS Data plane
By allowing Amazon EKS to manage some or all of your data plane, you can simplify your infrastructure and maintain standardization.
![[Pasted image 20251107103108.png]]
With Self-managed nodes, only the control plane is managed by EKS. 
With managed node groups, is always started and managed by you. You can still see all the resources being used in your AWS account, such as EC2 instances and Auto Scaling groups. You still get all of the control, security, and visibility, with less work.
With AWS Fargate you can focus on creating applications and have Amazon EKS fully manage your data plane
##### Using Fargate
To use Fargate with Amazon EKS, you must create Fargate profiles.
![[Pasted image 20251107103526.png]]
Fargate profiles specify which pods should be scheduled on Fargate. You can choose to run all your pods on Fargate or only some. Fargate profiles use selectors, which include a namespace and labels.

|                | Unmanaged Nodes | Managed Nodes        | Fargate         |
| -------------- | --------------- | -------------------- | --------------- |
| Units of work  | Pod and EC2     | Pod and EC2          | Pod             |
| Unit of charge | EC2             | EC2                  | Pod             |
| Host lifecycle | Customer        | AWS (SSH is allowed) | No visible host |
| Host:pods      | 1:many          | 1:many               | 1:1             |

#### Configuring EKS
There are three tasks to perform when building a cluster: 
- Secure your AWS environment
- Configure the VPC networking for the cluster
##### AWS shared responsability model
You can deep dive about [[Shared Responsibility Model]]. 
###### Shared responsability model with self-managed workers
![[Pasted image 20251107104316.png]]
###### Shared responsability model with managed node groups
![[Pasted image 20251107104406.png]]
###### Shared responsability model with AWS Fargate
![[Pasted image 20251107104433.png]]

##### Creating a cluster with eksctl
eksctl automates many of the steps involved in cluster and worker node creation. Here is an overview of the tasks performed by eksctl when it is run with the default option: 

- Creates IAM roles for the cluster and worker nodes.
- Creates a dedicated VPC with Classless Inter-Domain Routing (CIDR) 192.168.0.0/16.
- Creates a cluster and a nodegroup.
- Configures access to API endpoints.
- Installs CoreDNS.
- Writes a kubeconfig file for the cluster.

1. Step 1: Install eksctl
![[Pasted image 20251107114826.png]]
For more information, including examples of installing **eksctl** on other platforms, see [Getting started with Amazon EKS – **eksctl**](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html).
2. Step 2: Create a cluster
![[Pasted image 20251107114916.png]]
3. Step 3: View your nodes
![[Pasted image 20251107114941.png]]
##### Configuring horizontal and vertical scaling
Kubernetes has mechanisms to scale application workloads both vertically and horizontally.
###### Kubernetes automatic scaling
![[Pasted image 20251107143604.png]]
###### Cluster Autoscaler
The Kubernetes Cluster Autoscaler automatically adjusts the number of nodes in your cluster when pods fail to launch.
###### Karpenter: alternative to cluster autoscaler
Karpenter is a node lifecycle management solution. It observes incoming pods and launches the right instances for the situation.
When deployed, Karpenter will:
- Launch nodes for unscheduled pods.
- Replace existing nodes to improve resource utilization.
- Terminate nodes if outdated or no longer needed.
- Drain nodes gracefully before preemption.
###### Horizontal pod autoscaler
The Horizontal Pod Autoscaler (HPA) is a Kubernetes component that automatically scales your service in or out based on CPU utilization or other metrics that you define through the Kubernetes metrics server.
```
kubectl autoscale deployment myapp --cpu-percent=50 --min=1 --max=10
```
###### Vertical pod autoscaler
The Kubernetes Vertical Pod Autoscaler (VPA) automatically adjusts the CPU and memory reservations for your pods to help rightsize your applications. This adjustment can improve cluster resource utilization and free up CPU and memory for other pods.
 
#### Amazon EKS: Authentication and Authorization
The process for authenticating identities and authorizing commands is different for AWS commands and Kubernetes commands.

For AWS commands, such as **aws eks create-cluster**, the AWS IAM service handles both authentication and authorization. In this respect, Amazon EKS behaves just like other AWS services.
For Kubernetes commands, such as **kubectl get nodes**, Amazon EKS uses IAM user authentication to your Kubernetes cluster, but it relies on native Kubernetes RBAC for authorization. Using the IAM service for authentication simplifies cluster user management in two fundamental ways:

- Both IAM and Amazon EKS are integrated services managed by AWS.
- It addresses the issue of Kubernetes not providing end-user authentication.
![[Pasted image 20251107104701.png]]
##### Configuring permissions
There are three types of permissions to configure when deploying a new Amazon EKS cluster. 
- Cluster IAM Role: Amazon EKS requires permission to make calls to AWS APIs on your behalf to manage the cluster. This permission is controlled by the IAM role assigned to your cluster. AWS provides an IAM policy with the recommended permissions for this role.
- Node IAM Role: The **kubelet** daemon on Amazon EKS worker nodes makes calls to AWS APIs on your behalf; for example, pulling container images from the Amazon Elastic Container Registry (Amazon ECR).### Introduction to Kubernetes
- RBAC user: The administrators who will manage your Kubernetes cluster need permission to make calls to the Kubernetes API. This is accomplished by mapping an IAM role to a Kubernetes RBAC user.
##### Configuring networking
Before creating an Amazon EKS cluster, you must decide whether you will use one of your existing Amazon VPCs or if you will create a new VPC for your Amazon EKS cluster.
VPCs for Amazon EKS clusters can use one of three common design patterns:

- Only public subnets: This VPC has three public subnets at most that are deployed into different Availability Zones in the Region. All worker nodes are automatically assigned public IP addresses and can send and receive internet traffic through an internet gateway. A security group is deployed that denies all inbound traffic and allows all outbound traffic.
![[Pasted image 20251107114101.png]]
- Only private subnets: This VPC has three private subnets at most that are deployed into different Availability Zones in the Region. All nodes can optionally send and receive internet traffic through a network address translation (NAT) instance or NAT gateway. A security group is deployed that denies all inbound traffic and allows all outbound traffic. The NAT gateway in each Availability Zone deployment pattern is a recommended practice for meeting high availability requirements.
- Public and private subnets: This VPC has two public subnets and two private subnets. One public and one private subnet are deployed to the same Availability Zone. The other public and private subnets are deployed to a second Availability Zone in the same Region. We recommend this option for all production deployments.
	- For more information about subnet tagging, see [Subnet tagging](https://docs.aws.amazon.com/eks/latest/userguide/network_reqs.html#vpc-subnet-tagging) requirements in the _Amazon EKS User Guide_.
	- For more information about this type of VPC, see [VPC with public and private subnets (NAT)](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html) in the _A__mazon VPC User Guide_.
![[Pasted image 20251107114304.png]]

#### Managing communication in Amazon EKS
To simplify inter-node communication, Amazon EKS integrates Amazon VPC networking into Kubernetes through the Amazon VPC Container Network Interface (CNI) plugin for Kubernetes.
The are multiple types of communication in Amazon EKS environments. 
- Intrapod communication: Containers in a pod share a Linux namespace and can communicate with each other using localhost. In Kubernetes networking, the IP address with which a container identifies is the same IP address for all entities in the network.
![[Pasted image 20251107145330.png]]
- Intrahost communication: In addition to each pod having a Linux namespace, the host node also has a Linux namespace. Each namespace has its own routing table. The pod namespace and host namespace are connected by a Linux virtual Ethernet (veth) device. A pair of veths creates a tunnel between the default host namespace and the pod namespace.
![[Pasted image 20251107145433.png]]
- Interhost communication: Amazon VPC CNI plugin allows Kubernetes pods to have the same IP address inside the pod as they do on the Amazon VPC network. CNI uses the Amazon EC2 ability to provision multiple network interfaces to a host instance—each with multiple secondary IP addresses—to get multiple IP addresses assigned from the Amazon VPC pool. It then distributes these IP addresses to pods on the host and connects the network interface to the veth port created on the pod.
![[Screenshot 2025-11-07 145700.png]]
##### Ingress objects
With Kubernetes ingress objects, you can reduce the number of load balancers you use. An ingress object exposes HTTP and HTTPS routes from outside the cluster to your services and defines traffic rules.
![[Pasted image 20251107150323.png]]
##### AWS Load Balancer Controller
The AWS Load Balancer Controller is a controller that manages Elastic Load Balancing (ELB) for a Kubernetes cluster. The load balancers can be Application Load Balancers when you create a Kubernetes Ingress or Network Load Balancers when you create a Kubernetes service of type LoadBalancer.
An Application Load Balancer balances application traffic at Layer 7 (for example, HTTP or HTTPS) of the Open Systems Interconnection (OSI) model, while a Network Load Balancer balances network traffic at Layer 4
### Kubernetes objects
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services. By bringing software development and operations together by design, Kubernetes created a rapidly growing ecosystem that is very popular and well established in the market.

- **Cluster**: A set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node. A cluster also has a control plane that runs services that manage the cluster.
- **Node**: Kubernetes runs your workload by grouping containers into pods and assigning those pods to run on nodes. A node can be a virtual or physical machine, depending on the cluster. Each node is managed by the control plane.
- **Pod**: A group of one or more containers. Pods are defined by a PodSpec file, a specification for how to run the containers.
- **Ephemeral volume**: Applications in a pod have access to shared volumes to facilitate data sharing in the pod and persistence of data across container restarts. When a pod ceases to exist, Kubernetes destroys ephemeral volumes.
- **Persistent volumes**: A persistent volume functions similarly to an ephemeral volume but has a lifecycle independent of any individual pod that uses them.
- **Service**: In Kubernetes, a service is a logical collection of pods and a means to access them. The service is continually updated with the set of pods available, eliminating the need for pods to track other pods.
- **Namespace**: A virtual cluster that is backed by the same physical cluster. Physical clusters can have resources with the same name as long as they are in different namespaces.
![[Pasted image 20251107100514.png]]
- **Replica set**: Ensures that a specific number of pod replicas are running at any given time.
![[Pasted image 20251107100526.png]]
- **Deployment**: Owns and manages ReplicaSets or individual pods. You describe a desired state in the deployment. The deployment then changes the actual state of the cluster to the desired state at a controlled rate.
![[Pasted image 20251107100601.png]]
- **Config map**: A ConfigMap is an API object that stores nonconfidential data as key-value pairs used by other Kubernetes objects, such as pods.
- **Secrets**: All confidential data, such as AWS credentials, should be stored as Kubernetes secrets. Secrets restrict access to sensitive information. Optionally, encryption can be turned on to improve security.
![[Pasted image 20251107100646.png]]
#### Pod scheduling
You can schedule pods with the Kubernetes scheduler. The scheduler checks the resources required by your pods and uses that information to influence the scheduling decision. The scheduler runs a series of filters to exclude ineligible nodes for pod placement.
![[Pasted image 20251107101019.png]]
#### Control plane and data plane
**Control plane:** Control plane nodes manage the worker nodes and the pods in the cluster.

**Data plane:** Worker nodes host the pods that are the components of the application workload.
![[Pasted image 20251107101254.png]]
#### Custom resources
In addition to the resources that Kubernetes defines (such as pods and deployments), you can also extend the Kubernetes API and create custom resources. A custom resource could be a new object, such as a service mesh object, or it can be a combination of native Kubernetes resources. Custom resources are created with a Custom Resource Definition (CRD).
#### Kubectl
You can communicate with your control plane nodes using kubectl. kubectl is a command line interface (CLI) for communicating with the Kubernetes API server.
```
kubectl [commands] [TYPE] [NAME] [flags]
```
### Resources ECS and EKS
- AWS website: [Containers on AWS(opens in a new tab)](https://aws.amazon.com/containers/services/)
- External website: [Docker: Use Containers to Build, Share and Run Your Applications(opens in a new tab)](https://www.docker.com/resources/what-container)
- AWS website: [Amazon Elastic Container Service (Amazon ECS)(opens in a new tab)](https://aws.amazon.com/ecs/)
- External website: [Github: Amazon ECS Agent(opens in a new tab)](https://github.com/aws/amazon-ecs-agent)
- AWS developer guide: [Amazon ECS Container Instances(opens in a new tab)](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_instances.html)
- External website: [Coursera course: Building Containerized Applications on AWS(opens in a new tab)](https://www.coursera.org/learn/containerized-apps-on-aws)
- AWS website: [Amazon Elastic Kubernetes Service (EKS)(opens in a new tab)](https://aws.amazon.com/eks/)
- AWS user guide: [Amazon EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)
- [Website eksctl]( https://eksctl.io/)
- [Cluster VPC considerations](https://docs.aws.amazon.com/eks/latest/userguide/network_reqs.html)
- [**eksctl** repository on GitHub](https://github.com/weaveworks/eksctl) provides access to additional documentation, YAML manifests, and the source code.
