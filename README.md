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
?

### 7. ReplicaSet
- A ReplicaSet is associated with Pod and indicates how many pod should be running within cluster.
- A ReplicaSrt implies a controller that atches the ongoing state.

### 8. Deployments
- Most recommended way to run code on kubernetes is via Deployments.

### 9. Services
- Service is Kubernetes Resource used ot provide an abstraction through to your pods agnostic of the specific instance that are running.
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

## Azure Container Registry
Azure Container Registry allows you to store images for all types of container deployments including DC/OS, Docker Swarm, Kubernetes, and Azure services such as App Service, Batch, Service Fabric, and others. Your DevOps team can manage the configuration of apps isolated from the configuration of the hosting environment.

### Development Roadmap of Azure Container Regoistry

![img text](https://github.com/milindchavan12/aks/blob/master/assets/ACR%20Roadmap.png)

## Steps to create ACR via Azure CLI

Please login to azure cli with `az login` commmand

### 1. Create New Resource Group 
`az group create -n  letskube-rg -l westeurope`

### 2. Create ACR
`az acr create -n letskubeMilind -g letskube-rg -l westeurope --sku Standard`

### 3. To show all the ACR list
`az acr list -o table`

If a default resource group is set, that's the resource group that will be used for `az acr list -o table`, then remove the default `az configure --defaults group=''`

## Steps to Push local docker image to ACR Repository :

### 4. To login to Container Registry
`az acr login -n letskubeMilind`

### 5. Tag the local docker image

To upload the local docker image, we need to first tag it by Login Server name of the image.

`docker tag letskube:local letskubemilind.azurecr.io/letskube:v1`

The result of the Local and tagged image :

![img text](https://github.com/milindchavan12/aks/blob/master/assets/tagging.png)

### 6. Push the docker image
`docker push letskubemilind.azurecr.io/letskube:v1`

Output :

![img text](https://github.com/milindchavan12/aks/blob/master/assets/docker-push.png)

### 7. Verify indeed the image pushed to repository

`az acr repository list -n letskubeMilind -o table`

