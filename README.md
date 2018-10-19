# Kubernetes

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications." - Primary definition from https://kubernetes.io/

- Kubernetes exposes the underlying infrastructure as a singel computational resource.
- Consistent deployment exprience regardless of the size og the cluster.

![img text](https://github.com/milindchavan12/aks/blob/master/assets/KubeArchitecture.png)

## Running the Application in Kubernetes

![img text](https://github.com/milindchavan12/aks/blob/master/assets/RunApp.png)

## Kubernetes Objects

### 1. kubectl
Kubectl is command line interface for running commands against Kubernetes cluster.

### 2. pods
- Pod is smallest unit that Kubernetes manages and is fundamental unit on which rest of the Kubernetes system build on.
- Made of one of more containers and information associated with these containers.

### 3. Namespaces
- Pods are collected into Namespaces, which are used to group pods.
- Namespaces can be used to provide qoutas and limits around resource usage.

### 4. nodes
- Node is machine (linux) that is added to the kubernetes cluster.
- Master node is the Brain of Kubernetes while Worker nodes (minions) do the real work.

### 5. Networks 
- All containers in pod share a Node's network
- All nodes in Kubernetes cluster are expected to be connected to each and share a private cluster-wide network.

### 6. Controllers 
- ReplicationController ensures that specified number of pod replicas are running at any one time

### 7. ReplicaSet
- A ReplicaSet is associated with Pod and indicates how many pod should be running within cluster.
- A ReplicaSrt implies a controller that atches the ongoing state.

### 8. Deployments
- Most recommended way to run code on kubernetes is via Deployments.

### 9. Services
- Service is Kubernetes Resource used to provide an abstraction through to your pods agnostic of the specific instance that are running.
- Emulates the software load balancer within kubernetes.

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


