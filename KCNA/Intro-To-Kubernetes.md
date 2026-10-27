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


