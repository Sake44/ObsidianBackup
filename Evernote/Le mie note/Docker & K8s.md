---
---
## Cheat-sheet on Docker

* A container is a unit of software that encapsulates everything needed to build, ship, and run applications.  
* Containers lower deployment time and costs, improve utilization, automate processes, and support next-gen applications (microservices). Major container vendors include Docker, Podman,
	LXC, and Vagrant. 
	
* Docker is an open platform used for developing, shipping, and running applications as containers. 
* Docker containers are not a good fit for applications based on monolithic architecture or applications that require high performance or security. 
* Docker architecture consists of the Docker client, the Docker host, and the container registry. 
* The Docker host contains objects such as the Dockerfiles, images, containers, networks, storage volumes, and other objects, such as plugins and add-ons. 
* Docker uses networks to isolate container communications. 
* Docker uses volumes and binds mounts to persist data even after a container stops running. 
* Plugins, such as storage plugins, provide the ability to connect to external storage platforms. 

![[./_resources/Docker_&_K8s.resources/image.png]]

## **Container glossary**

|     |     |
| --- | --- |
| **Term** | **Definition** |
| **Agile** | is an iterative approach to project management and software development that helps teams deliver value to their customers faster and with fewer issues. |
| **Client-server architecture** | is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters, called clients. |
| **A container** | powered by the containerization engine, is a standard unit of software that encapsulates the application code, runtime, system tools, system libraries, and settings necessary for programmers to efficiently build, ship and run applications. |
| **Container Registry** | Used for the storage and distribution of named container images. While many features can be built on top of a registry, its most basic functions are to store images and retrieve them. |
| **CI/CD pipelines** | A continuous integration and continuous deployment (CI/CD) pipeline is a series of steps that must be performed in order to deliver a new version of software. CI/CD pipelines are a practice focused on improving software delivery throughout the software development life cycle via automation. |
| **Cloud native** | A cloud-native application is a program that is designed for a cloud computing architecture. These applications are run and hosted in the cloud and are designed to capitalize on the inherent characteristics of a cloud computing software delivery model. |
| **Daemon-less** | A container runtime that does not run any specific program (daemon) to create objects, such as images, containers, networks, and volumes. |
| **DevOps** | is a set of practices, tools, and a cultural philosophy that automate and integrate the processes between software development and IT teams. |
| **Docker** | An open container platform for developing, shipping and running applications in containers. |
| **A Dockerfile** | is a text document that contains all the commands you would normally execute manually in order to build a Docker image. Docker can build images automatically by reading the instructions from a Dockerfile. |
| **Docker client** | is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon. |
| **Docker Command Line Interface (CLI)** | The Docker client provides a command line interface (CLI) that allows you to issue build, run, and stop application commands to a Docker daemon. |
| **Docker daemon (dockerd)** | creates and manages Docker objects, such as images, containers, networks, and volumes. |
| **Docker Hub** | is the world's easiest way to create, manage, and deliver your team's container applications. |
| **Docker localhost** | Docker provides a host network which lets containers share your host’s networking stack. This approach means that a localhost in a container resolves to the physical host, instead of the container itself. |
| **Docker remote host** | A remote Docker host is a machine, inside or outside our local network which is running a Docker Engine and has ports exposed for querying the Engine API. |
| **Docker networks** | help isolate container communications. |
| **Docker plugins** | such as a storage plugin, provides the ability to connect external storage platforms. |
| **Docker storage** | uses volumes and bind mounts to persist data even after a running container is stopped. |
| **LXC** | LinuX Containers is a OS-level virtualization technology that allows creation and running of multiple isolated Linux virtual environments (VE) on a single control host. |
| **IBM Cloud Container Registry** | stores and distributes container images in a fully managed private registry. |
| **Image** | An immutable file that contains the source code, libraries, and dependencies that are necessary for an application to run. Images are templates or blueprints for a container. |
| **Immutability** | Images are read-only; if you change an image, you create a new image. |
| **Microservices** | are a cloud-native architectural approach in which a single application contains many loosely coupled and independently deployable smaller components or services. |
| **Namespace** | A Linux namespace is a Linux kernel feature that isolates and virtualizes system resources. Processes which are restricted to a namespace can only interact with resources or processes that are part of the same namespace. Namespaces are an important part of Docker’s isolation model. Namespaces exist for each type of resource, including networking, storage, processes, hostname control and others. |
| **Operating System Virtualization** | OS-level virtualization is an operating system paradigm in which the kernel allows the existence of multiple isolated user space instances, called containers, zones, virtual private servers, partitions, virtual environments, virtual kernels, or jails. |
| **Private Registry** | Restricts access to images so that only authorized users can view and use them. |
| **REST API** | A REST API (also known as RESTful API) is an application programming interface (API or web API) that conforms to the constraints of REST architectural style and allows for interaction with RESTful web services. |
| **Registry** | is a hosted service containing repositories of images which responds to the Registry API. |
| **Repository** | is a set of Docker images. A repository can be shared by pushing it to a registry server. The different images in the repository can be labelled using tags. |
| **Server Virtualization** | Server virtualization is the process of dividing a physical server into multiple unique and isolated virtual servers by means of a software application. Each virtual server can run its own operating systems independently. |
| **Serverless** | is a cloud-native development model that allows developers to build and run applications without having to manage servers. |
| **Tag** | A tag is a label applied to a Docker image in a repository. Tags are how various images in a repository are distinguished from each other. |

## Detailed means

**What is the Docker daemon?**

The Docker daemon runs on a host and listens for API calls to manage Docker objects. For example, if you want to build an image, run a container, or create a volume, you can use the Docker command line interface (CLI) to create the request. The request will then be submitted to the Docker daemon to be managed.

**What is the Docker CLI?**

The Docker command line interface (CLI) is the client interface for interacting with Docker objects. The Docker CLI is how you issue commands to Docker to build your containers, run your containers, or stop your containers.

**What is a Dockerfile?**
A Dockerfile is a text document that contains instructions on how to build your container image. A Dockerfile includes instructions for what base layer to use (for example, whether you want to use a minimal version of Linux or use an image that has preinstalled software, such as a database engine). Other instructions include running commands in the container, or copying your application data, dependencies, and configurations into the container. For more information, see [Best Practices for writing Dockerfile](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)s.

**What is a Docker image?**
A container image is created when you run the build command from the Docker CLI and it follows the instructions in a Dockerfile. A container image is made up of a series of read-only layers, with one writable layer on top where files can be added, modified, or deleted. Each layer is created from an instruction in the Dockerfile.

**What is an image registry?**
An image registry is a repository where you can store container images. You can store the images either publicly or privately. From the repository, images can be pulled and deployed, or used by other developers.

## How to containerize a Spring boot application

**1\. Prepare the Spring Boot Application**
		Make sure your Spring Boot application is ready and working. Generate an executable JAR file using Maven or Gradle.

Example with Maven:
```
mvn clean package
```

This command will generate a JAR file in the \`target\` directory.

**2\. Write the Dockerfile**
Create a file named \`Dockerfile\` in the root of your project. This file contains the instructions on how Docker should build the image.

Example \`Dockerfile\` for a Spring Boot application:

```
# Use a base JDK image
FROM openjdk:17-jdk-slim
# Add a label to the image
LABEL maintainer="your_name@example.com"
# Create a directory for the application
RUN mkdir /app
# Copy the application JAR file to the container
COPY target/your-application.jar /app/your-application.jar
# Expose the port the application will run on
EXPOSE 8080
# Command to run the application
ENTRYPOINT ["java", "-jar", "/app/your-application.jar"]
```

**3\. Build the Docker Image**
		Use the \`docker build\` command to create the Docker image.

Example:
```
docker build -t image-name:version .
```
For example:
```
docker build -t spring-boot-app:1.0 .
```

**4\. Run the Container**
		Once the image is built, you can run the container using the \`docker run\` command.

Example:
```
docker run -p 8080:8080 image-name:version
```
For example:
```
docker run -p 8080:8080 spring-boot-app:1.0
```

5\. Verify the Application
Open your browser and navigate to \`http://localhost:8080\` to verify that the Spring Boot application is running inside the Docker container.

### Additional Considerations

\- **Docker Compose**:
		If your application depends on other services (e.g., databases), consider using Docker Compose to manage multiple containers.
\- **Configuration**: Use environment variables for dynamic configurations within the container.
\- **Image Optimization**: Reduce the Docker image size by using lighter base images such as \`adoptopenjdk\` or \`alpine\`.

\### Using \`docker init\`
Yes, you can use \`docker init\` to quickly set up Docker for your project. Here are the steps:

1\. Navigate to your project directory:
```
cd /path/to/your/project
```

2\. Run the \`docker init\` command:
```
docker init
```

This command will generate a \`Dockerfile\` and other necessary configuration files in your project directory.

#### Differences Between Manual Approach and `docker init`

|     |     |     |
| --- | --- | --- |
| Aspect | Manual Approach | `docker init` |
| Control | Maximum control over every detail of the `Dockerfile` | Limited to the standard configurations provided during initialization |
| Customization | Complete customization possible | Customization based on the options provided during initialization |
| Ease of Use | Requires detailed knowledge of Docker and best practices | Easier to use, suitable for beginners |
| Setup Time | More time-consuming to manually write the files | Reduced setup time due to automation |
| Flexibility | Can be tailored to any specific project requirements | Suitable for standard configurations, might need further modifications |

**Conclusion**
Both approaches have their merits. If you're new to Docker or want to get started quickly, \`docker init\` is an excellent choice. If you have specific needs or want detailed control, the manual approach is preferable.

## Docker command

|     |     |
| --- | --- |
| Command | Description |
| docker ps -a | List container |
| docker ps | List images |
| docker exec -it (FIRST TWO CHAR OF CONTAINER ID) sh | Execute a shell in the container |
| docker images | List all images |
| docker rmi <tag image> | Remove image |
| docker system prune<br>USE CAREFULLY | doing general clean-up. This<br>will remove all stopped containers, all untagged images, and all unused image layers<br>cached as part of the build process. |
| docker run -ti rockylinux:8 | Run a docker image base on RockyLinux.<br>**\-ti** log-in in our instance to access interactive shell |
| docker build | Buil an image from a Dockerfile |
| docker tag <image id> username/repository:version | Tag an image using it's ID |

## [Configure Docker to start on boot with systemd](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd)

Many modern Linux distributions use [systemd](https://docs.docker.com/config/daemon/systemd/) to manage which services start when the system boots. On Debian and Ubuntu, the Docker service starts on boot by default. To automatically start Docker and containerd on boot for other Linux distributions using systemd, run the following commands:

```
$ sudo systemctl enable docker.service

$ sudo systemctl enable containerd.service


```

To stop this behavior, use disableinstead.

```
$ sudo systemctl disable docker.service

$ sudo systemctl disable containerd.service


```

If you need to add an HTTP proxy, set a different directory or partition for the Docker runtime files, or make other customizations, see [customize your systemd Docker daemon options](https://docs.docker.com/config/daemon/systemd/).

# Basic K8s

Kubernetes è un sistema open source per l'orchestrazione dei container, che permette di automatizzare il deployment, il scaling e la gestione delle applicazioni containerizzate. Comprendere i suoi principi fondamentali e i componenti chiave è essenziale per utilizzare Kubernetes in modo efficace. Ecco una panoramica dettagliata dei componenti chiave che hai menzionato:

## Principi fondamentali di Kubernetes

Automazione: Kubernetes automatizza molti aspetti della gestione dei container, inclusi il deployment, la scalabilità e l'auto-riparazione dei container. Ciò riduce la necessità di intervento manuale e consente una gestione più efficiente delle applicazioni.

Scalabilità: Kubernetes facilita la scalabilità delle applicazioni attraverso il clustering dei nodi e il bilanciamento del carico. Supporta la scalabilità sia verticale che orizzontale, adattando le risorse in base alla domanda.

Resilienza: Kubernetes è progettato per garantire la disponibilità e l'affidabilità delle applicazioni. Gestisce automaticamente i guasti dei nodi, riavviando i container falliti e ridistribuendo i carichi di lavoro in modo che l'applicazione rimanga sempre disponibile.

Portabilità: Le applicazioni containerizzate in Kubernetes possono essere eseguite su diverse piattaforme e cloud, fornendo un ambiente coerente per lo sviluppo e la produzione.

Manutenibilità: Kubernetes supporta il monitoraggio e la registrazione delle applicazioni, permettendo una gestione proattiva delle prestazioni e la risoluzione dei problemi. I suoi strumenti integrati aiutano nella gestione delle configurazioni e negli aggiornamenti.

## Componenti fondamentali di K8s

|     |     |     |
| --- | --- | --- |
| Nome | Funzionalita\` | Descrizione |
| kubeadm | Inizializzazione del cluster.<br>Aggiunta di nuovi nodi al cluster.<br>Generazione di file di configurazione per il cluster.<br>Operazioni di aggiornamento e gestione del cluster. | è uno strumento di comando che semplifica l'installazione e la configurazione di un cluster Kubernetes. Fornisce un modo semplice per inizializzare un cluster Kubernetes su un nodo e aggiungere nodi aggiuntivi al cluster. |
| kubelet | Monitora lo stato dei container e li riavvia se necessario.<br>Comunica con l'API server per ricevere le specifiche dei Pod.<br>Gestisce il ciclo di vita dei Pod.<br>Raccolta e invio di metriche del nodo e dei Pod. | è un agente che gira su ciascun nodo nel cluster Kubernetes. È responsabile della gestione dei container su quel nodo. Il kubelet prende le istruzioni dal apiserver e garantisce che i container definiti nei Pod siano in esecuzione e sani. |
| apiserver (Kube-API Server) | Gestisce le richieste RESTful (creazione, aggiornamento, eliminazione, recupero di risorse).<br>Funziona come gateway per tutte le operazioni del cluster.<br>Assicura l'autenticazione e l'autorizzazione delle richieste.<br>Fornisce accesso ai dati di stato e configurazione. | Il server API è il componente principale che espone l'API Kubernetes. È il punto di ingresso per tutte le interazioni amministrative con il cluster. Tutti i componenti comunicano attraverso l'API server. |
| controller-manager | Replica Controller: gestisce il numero desiderato di repliche di un Pod.<br>Node Controller: monitora lo stato dei nodi e risponde ai guasti.<br>Endpoint Controller: gestisce gli endpoint di servizio.<br>Service Account & Token Controller: crea account di servizio e token per i Pod.<br>Molti altri controller che gestiscono specifiche risorse e aspetti del cluster. | Il controller manager è un demone che esegue i vari controller di Kubernetes, ognuno dei quali controlla lo stato delle risorse nel cluster. I controller agiscono per mantenere lo stato desiderato del sistema. |
| scheduler | Assegnazione dei Pod ai nodi disponibili.<br>Bilanciamento del carico di lavoro tra i nodi.<br>Considerazione delle restrizioni di posizionamento dei Pod.<br>Rispetto delle politiche di scheduling configurate. | Lo scheduler è il componente che decide su quale nodo eseguire ogni Pod non assegnato. Lo scheduler assegna i Pod ai nodi in base a diversi criteri, tra cui risorse disponibili, requisiti di affinità, tolleranze e altre politiche definite dall'utente. |

![[./_resources/Docker_&_K8s.resources/image.1.png]]

In sintesi, Kubernetes è composto da numerosi componenti che lavorano insieme per fornire una piattaforma potente per la gestione delle applicazioni containerizzate. La comprensione di kubeadm, kubelet, apiserver, controller-manager e scheduler è fondamentale per sfruttare appieno le capacità di Kubernetes.

### How YAML file is structured?

![[./_resources/Docker_&_K8s.resources/Screenshot from 2024-10-04 09-15-29.png]]

# Kubernetes Command

|     |     |
| --- | --- |
| Comando | Descrizione |
| kubectl get pods | Elenca tutti i pod nel namespace corrente. |
| kubectl get services | Elenca tutti i servizi nel namespace corrente. |
| kubectl get nodes | Elenca tutti i nodi nel cluster. |
| kubectl get deployments | Elenca tutti i deployment nel namespace corrente. |
| kubectl describe pod <pod> | Fornisce informazioni dettagliate su un pod specifico. |
| kubectl describe service <service> | Fornisce informazioni dettagliate su un servizio specifico. |
| kubectl describe node <node> | Fornisce informazioni dettagliate su un nodo specifico. |
| kubectl create -f <file> | Crea una risorsa da un file di configurazione YAML o JSON. |
| kubectl apply -f <file> | Applica i cambiamenti di configurazione a una risorsa esistente o crea una nuova risorsa da un file. |
| kubectl delete -f <file> | Elimina risorse definite in un file di configurazione. |
| kubectl delete pod <pod> | Elimina un pod specifico. |
| kubectl logs <pod> | Visualizza i log di un pod specifico. |
| kubectl exec -it <pod> -- <command> (ash / date etc..) | Esegue un comando all'interno di un pod in modalità interattiva. |
| kubectl scale deployment <deployment> --replicas=<num> | Scala un deployment al numero desiderato di repliche. |
| kubectl get namespaces | Elenca tutti i namespace nel cluster. |
| kubectl create namespace <namespace> | Crea un nuovo namespace. |
| kubectl config set-context --current --namespace=<namespace> | Imposta il namespace corrente per il contesto. |
| kubectl get events | Elenca gli eventi nel cluster. |
| kubectl port-forward <pod> <local\_port>:<remote\_port> | Inoltra una porta locale a una porta su un pod specifico. |
| kubectl apply -f <dir> | Applica tutte le configurazioni trovate in una directory. |
| kubectl rollout status deployment <deployment> | Visualizza lo stato del rollout di un deployment. |
| kubectl rollout undo deployment <deployment> | Annulla l'ultimo rollout di un deployment. |
| kubectl top nodes | Mostra l'uso delle risorse per i nodi. |
| kubectl top pods | Mostra l'uso delle risorse per i pod. |
| kubectl get pv | Elenca tutti i Persistent Volumes (PV). |
| kubectl get pvc | Elenca tutti i Persistent Volume Claims (PVC). |
| kubectl get componentstatuses | status cluster |
| sudo kubeadm init | initializes a Kubernetes control-plane node |
| sudo kubeadm join | initializes a Kubernetes worker node and joins it to the cluster |

Vediamo di chiarire meglio la gerarchia e le relazioni tra queste unità in Kubernetes:

1. **Pod**:

   - I Pod sono le unità di base di esecuzione che contengono i container.

2. **Node**:

   - I Pod vengono eseguiti sui nodi. Un nodo può essere una macchina fisica o virtuale.

3. **Cluster**:

   - Un cluster è costituito da un insieme di nodi (sia nodi di lavoro che nodi master/piano di controllo). I nodi all'interno di un cluster lavorano insieme per eseguire applicazioni containerizzate gestite da Kubernetes.

4. **Namespace**:

   - Un namespace è un modo per partizionare logicamente le risorse all'interno di un cluster. Serve a separare e isolare gruppi di risorse (Pod, servizi, ecc.) all'interno dello stesso cluster. Tuttavia, il namespace non contiene il cluster; piuttosto, esistono all'interno del cluster per organizzare e gestire le risorse.

### Relazioni Corrette

\- **Pod**: È contenuto in un **namespace** e viene eseguito su un **nodo**.
\- **Nodo**: È parte di un **cluster**.
\- **Namespace**: È una partizione logica all'interno di un **cluster**. I Pod, i servizi e altre risorse Kubernetes sono contenuti nei namespace.
\- **Cluster**: Contiene nodi e namespace. È l'entità più grande che gestisce l'intera infrastruttura Kubernetes.

**Schema Gerarchico Corretto:**

1\. **Cluster**
   - Contiene **Nodi**
     - Ogni **Nodo** esegue diversi **Pod**
   - Contiene **Namespace**
     - Ogni **Namespace** contiene risorse come **Pod**, **Servizi** **Deployments,** ecc.

In altre parole:
\- Un **Pod** è all'interno di un **namespace**
\- Un **Nodo** è parte di un **Cluster**
\- Un **Cluster** contiene sia i **Nodi** che i **Namespace**

Visualizzazione della gerarchia:

```
Cluster
├── Node1
│  ├── Pod1 (Namespace: default)
│  └── Pod2 (Namespace: default)
├── Node2
│  ├── Pod3 (Namespace: dev)
│  └── Pod4 (Namespace: prod)
└── Namespaces
    ├── default
    ├── dev
    └── prod
```

In questo schema:
\- I Pod sono assegnati ai nodi e sono parte di un namespace.
\- I nodi sono parte del cluster.
\- I namespace sono entità logiche all'interno del cluster che contengono le risorse Kubernetes.

# Basic Vagrantfile (VM ubuntu 20.04??)

Vagrant is the command line utility for managing the lifecycle of virtual machines. Isolate dependencies and their configuration within a single disposable and consistent environment.
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.hostname = "cp1"

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--cpuexecutioncap", "80",
      "--memory", "2048"
    ]
  end

#specific for image
config.vm.define "ubuntu1" do |ubuntu1|
    ubuntu1.vm.hostname = "ubuntu1"
end

end
```
