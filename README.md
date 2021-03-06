# Kubernetes

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications." - Primary definition from https://kubernetes.io/

In short **Kubernetes is Container Orchestrator**.

- Kubernetes exposes the underlying infrastructure as a singel computational resource.
- Consistent deployment exprience regardless of the size of the cluster.

![img text](https://github.com/milindchavan12/aks/blob/master/assets/KubeArchitecture.png)

## Kubernetes Concepts

### Cluster
A cluster is a collection of hosts storage and networking resources that Kubernetes uses to run the various workloads.

### Master
Master is the brain of Kubernetes. Command and query are coming to api-server via command line utility (kubectl). And depending upon the command and action, the execution is performed on Nodes.

![img text](https://github.com/milindchavan12/kubernetes/blob/master/assets/kube-master.png)

### Node
The Node is Kubernetes Worker/Machine added to Kubernetes Cluster. Node consists of 3 components:
- Kubelet : Is main kubernetes agent on the node. Exposes the endpoint on : 10255 port for inspecting the node.
- Container Engine : Does Container managment like Pulling images and starting/stoping containers.
- Kube-proxy : is Kubernetes networking, That means ONE IP per pode in container. Also Load Balances across all pods in a Service

### Pod
- Pod is smallest unit that Kubernetes manages and is fundamental unit on which rest of the Kubernetes system build on.
- Each pod contains one or more containers.
- Pods are *Emphemeral* - No pod is ever **Redeployed**

**Pod's LifeCycle** (Atomicity)
![img text](https://github.com/milindchavan12/aks/blob/master/assets/pod-lifecycle.png)

### Label
Labels are key-value pairs that are used to group together sets of objects. labels are dedicated for identifying objects and not for attaching arbitrary metadata to objects.

### Secret
Secrets are small objects that contain sensitive info such as credentials and tokens. They are stored as plaintext in **etcd**

### Namespaces
- Pods are collected into Namespaces, which are used to group pods.
- Namespaces can be used to provide qoutas and limits around resource usage.

### Services
- Service is Kubernetes Resource used to provide an **abstraction** through to your pods agnostic of the specific instance that are running.
- Emulates the software load balancer within kubernetes.
- Provides IP adn DNS for the service

![img text](https://github.com/milindchavan12/aks/blob/master/assets/service.png)

### Deployments
- Most recommended way to run code on kubernetes is via Deployments. Deployments are first class REST object in kubernetes API
  
  **ReplicaSet**
    - A ReplicaSet is associated with Pod and indicates how many pod should be running within cluster.
    - A ReplicaSet implies a controller that matches the ongoing state.

------------------------------------------------------------------------------------------------------------
## Kubernetes Cluster Network Ports
![img text](https://github.com/milindchavan12/kubernetes/blob/master/assets/networkports.png)


## Running the Application in Kubernetes

![img text](https://github.com/milindchavan12/aks/blob/master/assets/RunApp.png)

## Installing Minikube

### First of all install 'kubectl'
- On fresh install : `brew install kubectl`
- For update : `brew upgrade kubernetes-cli`

### Then Installing Minikube
- `brew cast install minikube`
- To use minikube vm xhyve : `brew install docker-machine-driver-xhyve`

### Start/Stop/Delete minikube
- To Start `minikube start --vm-driver=xhyve`
- To View dashboard `minikube dashboard`
- To Stop `minikube stop`
- To Delete `minikube delete`

------------------------------------------------------------------------------------------------------------
### Building the docker image
`
 docker build . -t <imageName>:local
`

### To view all the docker images
`
 docker image list
`

### To run docker image on local
`
docker run -d -p 5000:80 letskube:local
`

### To remove all docker instance on local
`
docker container rm -f $(docker ps -aq)
`


