---

tags: 
  - dry-run

---
# Using K8s API

API Server are the sole way to interact with your cluster and API objects are a collection of primitives which represent your system's state.
K8s API server is **client/server architecture** implemented as RESTful API over HTTP using JSON. Going to exchange JSON objects through RESTful.
Very important: K8s API server is stateless, that's mean all the changes made in the cluster are not stored in API server but in some db as **etcd (shared db that store the whole cluster's state).** Each HTTP request is handle as an indipendent operation.

## Control Plane Node

![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.png]]
In the control node we have a collection of critical services that help us facilitate cluster operations. Let's take a look to each of this services:

1. **API server** is the **primary access** point for administrative and cluster operations. It's the communication hub for the entire Kubernetes system.
2. **Cluster store** is where the state of the system is stored and persisted **(etcd)**
3. **The scheduler** tells Kubernetes which nodes to start Pods on based on Pod's resources requirements.
4. **Controller manager** is responsible for lifecycle functions of controllers, keeping things in desired state.

![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.1.png]]
The key players K8s API Objects (Kind) are **Pods, deployments, Services, PersistentVolumes (PV).**

|     |     |
| --- | --- |
| Kind | Definition |
| Pods | These are used to deploy our container-based in Kubernetes |
| Deployments | Allow us to declaratively deploy applications in our cluster and control our applications in terms of container image or version of our apps and also scale our app if needed |
| Services | Provide persistent access point and load balancing services for our applications running on pods. |
| PersistentVolumes (PV) | Provide persistent storage to our container-based apps |

A key principles to work with Kubernetes objects is the **declarative configuration.** That's mean we are going to define the **desired state of our application** in code using **manifest.** When we use manifests, we'll define our configurations in code using languages like YAML or JSON to represent the API objects we wwant to feed into our API server.

### Basic Manifest - pod

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: nginx
    image: nginx

// Then to execute

kubectl apply -f nginx.yml


```

### Working with Kubectl dry-run

When working with API objects and writing code to represent objects, we're going to need a way to ensure our code in these YAML file is sintatically correct and can be processed by the API successfully and here's where _dry-run_ parameter comes in.
There are two types of **_dry-run:_**

1. **Server-side:** the request is processed as an usual one except for one fundamental thing, the request will NOT be persisted in storage. Using **dry-run** enables you to know if the request you're submitting is properly formatted.
2. **Client-side:** dry-run will print the object that you want to create or change to **stdout** without sending the object API server.

```
// This will send the manifest .yaml to API server for server side validation.
kubectl apply -f deployment.yaml --dry-run=server

// This will NOT send the manifest .yaml to API server
kubectl apply -f deployment.yaml --dry-run=client

// Great way to gen syntatically-correct YAML manifests for any objects. Can be used as building block for more complex
kubectl create deployment -f nginx --image=nginx --dry-run=client -o yaml

//then we can add.. if everything is set properly
kubectl create deployment -f nginx --image=nginx --dry-run=client -o yaml > deployment.new.yaml

//Good base to generate correct yaml file of any object
kubectl create deployment -f nginx --image=nginx --dry-run=client -o yaml | more


```

![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.2.png]]

## 

## API Groups and API Versioning

### API groups

API groups enable better organization of resources in the Kubernetes API. There are two high-level organization methods for API groups in Kubernetes. The first is the CORE API (legacy) and the other one is Named API Groups.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.3.png]]

### API Versioning

API versioning helps us to build stable systems in our Kubernetes clusters. The kubernetes API is versioned at API level. In this way we know what version of the API we're interacting with when we define resources in code. If we're using declarative and building our system and code using objects to model it, this objects might change during time. Kubernetes provides us a mechanism to help us absorb that change when we're ready, that's API versioning.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.4.png]]

### 

## Anatomy of an API request

When we're working at command line with a tool like **kubectl,** we enter a command, and it'll convert from YAML to JSON. Since our API server is a RESTful HTTP web application,  we'll need to submit our request and specify a URL resource location or API path.
The K8s API is a client/server architecture where clients submit requests to the server. And primarly will be using **kubectl** to do this work, but really any HTTP client that respects the protocol set forth by the API server and the API itself will be able to communicate with the API server and submit request. This gives the ability to build custom tooling to interact with your Kubernetes cluster.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.7.png]]
There are some special API requests that can be made of the API server and facilitate cluster operations and workload management in our K8s cluster.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.8.png]]![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.9.png]]
When forward a request to API server we expect different response codes:
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.10.png]]![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.11.png]]

# 

### Useful commands API request

```
#Anatomy of an API Request
#Creating a pod with YAML
kubectl apply -f pod.yaml

#Get a list of our currently running Pods
kubectl get pod hello-world

#We can use the -v option to increase the verbosity of our request.
#Display requested resource URL. Focus on VERB, API Path and Response code
kubectl get pod hello-world -v 6
//Response
I1006 13:57:42.789949    6721 round_trippers.go:553] GET https://192.168.59.103:8443/api/v1/namespaces/default/pods/hello-world 200 OK in 4 milliseconds

#Same output as 6, add HTTP Request Headers. Focus on application type, and User-Agent
kubectl get pod hello-world -v 7

#Same output as 7, adds Response Headers and truncated Response Body.
kubectl get pod hello-world -v 8

#Same output as 8, add full Response. Focus on the bottom, look for metadata
kubectl get pod hello-world -v 9

#Start up a kubectl proxy session, this will authenticate use to the API Server
#Using our local kubeconfig for authentication and settings, updated head to only return 10 lines.
kubectl proxy &
curl http://localhost:8001/api/v1/namespaces/default/pods/hello-world | head -n 10

fg
ctrl+c

#Watch, Exec and Log Requests
#A watch on Pods will watch on the resourceVersion on api/v1/namespaces/default/Pods
kubectl get pods --watch -v 6 &

#We can see kubectl keeps the TCP session open with the server...waiting for data.
netstat -plant | grep kubectl

#Delete the pod and we see the updates are written to our stdout. Watch stays, since we're watching All Pods in the default namespace.
kubectl delete pods hello-world

#But let's bring our Pod back...because we have more demos.
kubectl apply -f pod.yaml

#And kill off our watch
fg
ctrl+c

#Accessing logs
kubectl logs hello-world
kubectl logs hello-world -v 6

#Start kubectl proxy, we can access the resource URL directly.
kubectl proxy &
curl http://localhost:8001/api/v1/namespaces/default/pods/hello-world/log

#Kill our kubectl proxy, fg then ctrl+c
fg
ctrl+c

#Authentication failure Demo
cp ~/.kube/config  ~/.kube/config.ORIG

#Make an edit to our username changing user: kubernetes-admin to user: kubernetes-admin1
vi ~/.kube/config

#Try to access our cluster, and we see GET https://172.16.94.10:6443/api?timeout=32s 403 Forbidden in 5 milliseconds
#Enter in incorrect information for username and password
kubectl get pods -v 6

#Let's put our backup kubeconfig back
cp ~/.kube/config.ORIG ~/.kube/config

#Test out access to the API Server
kubectl get pods

#Missing resources, we can see the response code for this resources is 404...it's Not Found.
kubectl get pods nginx-pod -v 6

#Let's look at creating and deleting a deployment.
#We see a query for the existence of the deployment which results in a 404, then a 201 OK on the POST to create the deployment which suceeds.
kubectl apply -f deployment.yaml -v 6

#Get a list of the Deployments
kubectl get deployment

#Clean up when we're finished. We see a DELETE 200 OK and a GET 200 OK.
kubectl delete deployment hello-world -v 6
kubectl delete pod hello-world
```

# 

# Managing objects with Labels, Annotations, and Namespaces

## Intro to Namespaces

Namespaces are a way of dividing a Kubernetes cluster into multiple virtual clusters. The first thing to know is that **Kubernetes Namespaces** are not the same as **Kernel Namespaces**:
• **Kernel namespaces** partition operating systems into virtual operating systems called containers
• **Kubernetes Namespaces** partition Kubernetes clusters into virtual clusters called Namespaces
Namespaces are a form of soft isolation and enable soft multi-tenancy. You can create Namespaces for your dev, test and qa environments and apply different quotas and policies to each.
Not all objects can be _namespaced_, such as **Nodes** and **PersistentVolumes**, are cluster-scoped and cannot be isolated to Namespaces.
```
kubectl api-resources
```

### Tenant definition

Tenant is a loose term and can refer to individual applications, different teams or departments, and even external customers. How you implement Namespaces and what you consider as tenants is up to you, but it’s most common to use Namespaces to divide clusters for use by tenants within the same organization.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.5.png]]
Namespaces are lightweight and easy to manage but only provide soft isolation.

## Default Namespaces

Every Kubernetes cluster has a set of pre-created Namespaces.
![[Evernote/My Notes/_resources/CKA_(Certified_K8s_Administrator).resources/image.6.png]]
The **default** Namespace is where new objects go if you didn't specify a Namespace when creating them. **kube-system** is where control plane components such as the internal DNS and the metrics server run. **kube-node-lease** is used for node heartbeat and managing node leases. **kube-public** is for objects that need to be readable by anyone.

## Labels

Labels are used to organize resources (Pods, Nodes). With labels we can leverage label selectors to select or query those objects, and doing this return a collection of objects that satisfy the search conditions that we provide in those label selectors. In this way we can perform operations on this collection of resources.
Labels are also used to influence internal operations of Kubernetes.

A label is a non-hierarchical key/value pair. We assing a key, we give it a value, and that is associate then to a resource in the cluster. Objects in Kubernetes can have more than a label per resource. This give us the ability to build more complex representation of the state of our system and query on those attributes or query on those labels associated with the objects in our cluster.
