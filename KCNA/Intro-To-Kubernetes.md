# CNCF (Cloud Native Computing Foundation)
Open source software stack to deploy microservices as containers and orchestrating containers for optimization



Includes projects like Kubernetes, Prometheus, and Envoy.

# Monolith
A design pattern of having an "all in one" service or software such as including a database, web frontend, and or backend all as one deployment rather than separating into components. Something like proxmox + a NAS is a monolith because it lacks fault tolerance while in theory it is not a monolith because it's not one big deployment or service but 2 services.


# Microservice
Breaking components up into smaller services that complete 1 to 2 tasks such as a database or metrics.

While it adds complexity it can be easier to trace issues and is easier to manage at scale.

Patching services individually reduces downtime because services won't be having 3+ components waiting to be healthy.

# Migrating to Microservices
A "big-bang" approach is described as halting feature development to focus on refactoring an application to microservice architecture.

An incremental approach is slowly developing new features as microservices or using microservice architecture.

# Challenges for Migrating
Many monoliths will not "survive" modernization or refactoring will be rejected for budgeting reasons.

Some cases it'd be easier/cheaper to rebuild from scratch instead of trying to use the existing one.

Fault tolerance may be difficult to achieve due to tightly coupled components.

Choosing runtimes can be difficult because of libraries or outdated dependencies or container images missing specific repositories/packages.

# Containers
Small isolated environments for an application that shares a kernel with the host. Containers use namespaces in linux to achieve isolation from the rest of the system.

Containers prevent dependency conflicts and allow for applications to be deployed anywhere without the "works on my machine" problem.


# Container Orchestration
Managing multiple containers at once using something like Kubernetes. 


# Container Orchestrators
* Amazon Elastic Container Service
* Azure Container Instances
* Azure Service Fabric
* Kubernetes
* Nomad
* Docker Swarm

Using Orchestrators allows for easier manageability at scale and reduces operational complexity when dealing with hundreds of containers as well as secure large scale deployments easily.

# Kubernetes
* Automatic binary packing with scheduling on the most available node at the time a pod was scheduled
* Extendable with custom API resources
* Self healing for failed pods or nodes ensuring high availability
* Horizontal scaling, allowing more applications to utilize resources efficiently without having to manually allocate resources.
* Automated rollouts and rollbacks being able to rollback changes or rollout changes
* Secret and config management with secret and config map objects
* Storage orchestration being able to utilize services like ceph or other distributed solutions with storage or having mounts like in docker.
* Batch execution like cronjobs and jobs
* IPv4 and IPv6 being able to use IPv4 and IPv6 in cluster without having to configure complex networking equipment

Portability and fault tolerance are the biggest strengths for Kubernetes making it the industry standard for container orchestration and even virtual machine orchestration.

Every major tech company uses Kubernetes in some capacity for their platform or as a service on their platform.

One of the biggest and most successful open source projects to date.

## Architecture
![linuxfoundation, Kubernetes architecture overview section in LFS158](https://d36ai2hkxl16us.cloudfront.net/course-uploads/e0df7fbf-a057-42af-8a1f-590912be5460/bpcsp24duwc1-TrainingImage.png)

## Nodes
### Control
* controls scheduling, ETCD (database of truth), controller managers and the Kube API
* control plane nodes can be workers

### Workers
* runs all pods and containers
* has kubelet and kube proxy
* Kubelet is the daemon for containers in Kubernetes that interacts with the container runtime
* Kube proxy receives updates and handles networking in Kubernetes for service networking across nodes (this is NOT the purpose of a CNI)
### CNI
* handles all pod networking

### CoreDNS
* Kubernetes DNS for services, pods, and endpoints to find one and another

### External Access to services
#### Ingress
* Manages external HTTP and HTTPS connections with virtual hosts
* Traefik is the standard

#### Load Balancer
* A virtual IP or VIP hosting various services such as ingress or plain HTTP that a node is broadcasting

#### Node port
* Exposing a service with a port on a node



## Installing Kubernetes
![](https://media.makeameme.org/created/one-does-not-bd145ab75f.jpg)
### Configuration
* All-in-one/Single node
  * all API components and worker components on one node
  * Good for development or super small deployments
  * Not fault tolerant
* Single control plane and Multi Worker
  * Multiple workers are controlled by single control plane
  * More fault tolerant than All in one
  * Control plane is not fault tolerant
  * Good for small deployments
* Multi Control plane and Worker
  * Very fault tolerant
  * Multiple control plane nodes control multiple workers
  * Considered "High Availability"/HA
  * Good for production environments catering to hundreds to thousands of users
* Multi Control Plane, Worker, and etcd
  * Multiple dedicated nodes for etcd
  * As fault tolerant as possible
  * Multiple etcd nodes ensure separation between control plane and etcd database
  * Good for environments catering to hundreds of thousands of users or more
  * Higher operational complexity




### Distributions
* Just like linux kubernetes has distributions
* Common ones include; Vanilla (Kubeadm), K3S, EKS, AKS, GKE, OpenShift, and Minikube.

