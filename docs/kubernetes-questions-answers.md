# Kubernetes Questions and Answers

{::options parse_block_html="true" /}

### <a name="Kubernetes-101">Kubernetes 101</a>

<details>
<summary markdown="span">What are the features of Kubernetes?</summary>

<p align="center">
  <img src="assets/k8s-features.png" alt="K8s Features" width="800px" />
</p>

</details>

<details>
<summary markdown="span">How is Kubernetes different from Docker Swarm?</summary>

- **Docker Swarm** is Docker’s native, open-source container orchestration platform that is used to cluster and schedule Docker containers. Swarm differs from Kubernetes in the following ways:
- **Docker Swarm** is more convenient to set up but doesn’t have a robust cluster, while Kubernetes is more complicated to set up but the benefit of having the assurance of a robust cluster
- Docker Swarm can’t do auto-scaling (as can Kubernetes); however, Docker scaling is five times faster than Kubernetes
- Docker Swarm doesn’t have a GUI; Kubernetes has a GUI in the form of a dashboard Docker Swarm does automatic load balancing of traffic between containers in a cluster, while Kubernetes requires manual intervention for load balancing such traffic
- Docker requires third-party tools like ELK stack for logging and monitoring, while Kubernetes has integrated tools for the same
Docker Swarm can share storage volumes with any container easily, while Kubernetes can only share storage volumes with containers in the same pod
- Docker can deploy rolling updates but can’t deploy automatic rollbacks; Kubernetes
can deploy rolling updates as well as automatic rollbacks

</details>

<details>
<summary markdown="span">How are Kubernetes & Docker related?</summary>

- Docker is an open-source platform used to handle software development.
- Its main benefit is that it packages the settings and dependencies that the software/application needs to run into a container, which allows for portability and several other advantages. Kubernetes allows for the manual linking and orchestration of several containers, running on multiple hosts that have been created using Docker.

</details>

<details>
<summary markdown="span">What is the difference between deploying applications on hosts & containers?</summary>

<p align="center">
  <img src="assets/hosts-containers.png" alt="Hosts Containers" width="800px" />
</p>

- Refer to the above diagram. The left side architecture represents deploying applications on hosts. So, this kind of architecture will have an operating system and then the operating system will have a kernel which will have various libraries installed on the operating system needed for the application. So, in this kind of framework you can have n number of applications and all the applications will share the libraries present in that operating system whereas while deploying applications in containers the architecture is a little different.
- This kind of architecture will have a kernel and that is the only thing that’s going to be the only thing common between all the applications. So, if there’s a particular application which needs Java then that particular application we’ll get access to Java and if there’s another application which needs Python then only that particular application will have access to Python.
- The individual blocks that you can see on the right side of the diagram are basically containerized and these are isolated from other applications. So, the applications have the necessary libraries and binaries isolated from the rest of the system, and cannot be encroached by any other application.

</details>

<details>
<summary markdown="span">What is Container Orchestration?</summary>

Consider a scenario where you have 5-6 microservices for an application.
Now, these microservices are put in individual containers, but won’t be able to communicate without container orchestration. So, as orchestration means the amalgamation of all instruments playing together in harmony in music, similarly container orchestration means all the services in individual containers working together to fulfill the needs of a single server.

</details>

<details>
<summary markdown="span">How does Kubernetes simplify containerized Deployment?</summary>

As a typical application would have a cluster of containers running across multiple hosts, all these containers would need to talk to each other. So, to do this you need something big that would load balance, scale & monitor the containers. Since Kubernetes is cloud-agnostic and can run on any public/private providers it must be your choice simplify containerized deployment.

</details>

<details>
<summary markdown="span">What do you know about clusters in Kubernetes?</summary>

The fundamental behind Kubernetes is that we can enforce the desired state management, by which I mean that we can feed the cluster services of a specific configuration, and it will be up to the cluster services to go out and run that configuration in the infrastructure.

<p align="center">
  <img src="assets/k8s-cluster.png" alt="K8s Cluster" width="800px" />
</p>

So, as you can see in the above diagram, the deployment file will have all the configurations required to be fed into the cluster services. Now, the deployment file will be fed to the API and then it will be up to the cluster services to figure out how to schedule these pods in the environment and make sure that the right number of pods are running.
So, the API which sits in front of services, the worker nodes & the Kubelet process that the nodes run, all together make up the Kubernetes Cluster.

</details>

<details>
<summary markdown="span">What is a Pod in Kubernetes?</summary>

A cluster of one or more Linux containers makes up a Kubernetes pod, the smallest unit of a Kubernetes application. From the more common scenario of a single container to an advanced use case with numerous tightly coupled containers within a pod, this basic structure allows for an array of designs.

```bash
kubectl get pods -n <namespace-name>
```

</details>

<details>
<summary markdown="span">What is Kubectl?</summary>

Kubectl is the platform using which you can pass commands to the cluster.
So, it basically provides the CLI to run commands against the Kubernetes cluster with various ways to create and manage the Kubernetes
component.

</details>

<details>
<summary markdown="span">What is Kubelet?</summary>

Consider a scenario where you have 5-6 microservices for an application.
Now, these microservices are put in individual containers, but won’t be able to communicate without container orchestration. So, as orchestration means the amalgamation of all instruments playing together in harmony in music, similarly container orchestration means all the services in individual containers working together to fulfill the needs of a single server.

</details>

<details>
<summary markdown="span">What is etcd?</summary>

Etcd is written in Go programming language and is a distributed key-value store used for coordinating between distributed work. So, Etcd stores the configuration data of the Kubernetes cluster, representing the state of the cluster at any given point in time.

</details>

<details>
<summary markdown="span">What are the different services within Kubernetes?</summary>

The following are the different types of services used:

<p align="center">
  <img src="assets/k8s-services.png" alt="K8s Services" width="800px" />
</p>

</details>

<details>
<summary markdown="span">What is the role of a pod?</summary>

A: A pod in Kubernetes is responsible for holding individual containers. Each pod can hold various containers depending on the configurations and requirements. The containers held within a single pod share the same resources and the same local network, which makes it easier for them to communicate.

</details>


<details>
<summary markdown="span">What is the LoadBalancer in Kubernetes?</summary>

A load balancer is one of the most common and standard ways of exposing service. There are two types of load balancer used based on the working environment i.e. either the Internal Load Balancer or the External Load Balancer. The Internal Load Balancer automatically balances load and allocates the pods with the required configuration whereas the External Load Balancer directs the traffic from the external load to the backend pods.

</details>

### <a name="ARCHITECTURE BASED QUESTIONS">ARCHITECTURE BASED QUESTIONS</a>

<details>
<summary markdown="span">What are the different components of Kubernetes Architecture?</summary>

The Kubernetes Architecture has mainly 2 components – the master node and the worker node. As you can see in the below diagram, the master and the worker nodes have many inbuilt components within them. The master node has the kube-controller-manager, kube-apiserver,
kube-scheduler, etcd. Whereas the worker node has kubelet and kube-proxy running on each node

<p align="center">
  <img src="assets/k8s-arch.png" alt="Docker Architecture" width="800px" />
</p>

<p align="center">
  <img src="assets/kubernetes-architecture.png" alt="Docker Architecture" width="800px" />
</p>

</details>

<details>
<summary markdown="span">What are the various K8 related services running on nodes and role of each service?</summary>

Mainly K8 cluster consists of two type of nodes: master and executor

- master services:
  - kube-apiserver: Master API service which acts like a door to K8 cluster. 
  - kube-scheduler: Schedule PODs according to available resources on executor nodes. 
  - kube-controller-manager: controller is a control loop that watches the shared state of the cluster through the 
    apiserver and makes changes attempting to move the current state towards the desired state

- executor node: (These also runs on master node)
  - kube-proxy: The Kubernetes network proxy runs on each node. This reflects services as defined in the Kubernetes API on 
    each node and can do simple TCP, UDP, and SCTP stream forwarding or round robin TCP, UDP, and SCTP forwarding across a set of backends.
  - kubelet: kubelet takes a set of PodSpecs that are provided through various mechanisms (primarily through the 
    apiserver) and ensures that the containers described in those PodSpecs are running and healthy

</details>

### <a name="Technical Questions">Technical QUESTIONS</a>

<details>
<summary markdown="span">What is the difference between config map and secret? (Differentiate the answers as with examples)</summary>

Config maps ideally stores application configuration in a plain text format whereas Secrets store sensitive data like password in an encrypted format. Both config maps and secrets can be used as volume and mounted inside a pod through a pod definition file.

- Configmap
```bash
kubectl create configmap myconfigmap --from-literal=env=dev
```

- Secret
```bash
echo -n ‘admin’ > ./username.txt
echo -n ‘abcd1234’ ./password.txt
kubectl create secret generic mysecret --from-file=./username.txt --from-file=./password.txt
```

<p align="center">
  <img src="assets/configmap-secrets.png" alt="Docker Architecture" width="800px" />
</p>

</details>

<details>
<summary markdown="span">How to control the resource usage of a POD?</summary>

With requests and limits resource usage of a POD can be control. 

request: the amount of resources being requested for a container. If a container exceeds its request for resources, it may be throttled back down to it’s request.

limit: an upper cap on the resources a container is able to use. If it tries to exceed this limit it may be terminated if Kubernetes decides that another container needs the resources. If you’re sensitive to pod restarts, it makes sense to have the sum of all container resource limits equal or less than the total resource capacity for your cluster.

</details>

<details>
<summary markdown="span">Recommended way of managing the access to multiple clusters?</summary>

kubectl looks for the config file, multiple clusters access information can be specified in this config file. `kubectl config` commands can be used to manage the access to these clusters.

</details>


<details>
<summary markdown="span">What is PDB (Pod Disruption Budget)?</summary>

A PDB specifies the number of replicas that an application can tolerate having, relative to how many it is intended to have. For example, a Deployment which has a .spec.replicas: 5 is supposed to have 5 pods at any given time. If its PDB allows for there to be 4 at a time, then the Eviction API will allow voluntary disruption of one, but not two pods, at a time. This is applicable for voluntary disruptions.

</details>

<details>
<summary markdown="span">How to troubleshoot if the POD is not getting scheduled?</summary>

There are many factors which can led to unstartable POD. Most common one is running out of resources, use the commands like `kubectl desribe <POD> -n <Namespace>` to see the reason why POD is not started. Also, keep an eye on `kubectl get events` to see all events coming from the cluster.

</details>

<details>
<summary markdown="span">What are the taints and toleration?</summary>

Taints allow a node to repel a set of pods. You can set taints on the node and only the POD which have tolerations matching the taints condition will be able to run on those nodes. This is useful in the case when you allocated node for one user and don't want to run the PODs from other users on that node. 

</details>