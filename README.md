# AKS : Azure Kubernetes Service

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications." - Primary definition from https://kubernetes.io/

- Kubernetes exposes the underlying infrastructure as a singel conputational resource.
- Consistent deployment exprience regardless of the size og the cluster.

![img text](https://github.com/milindchavan12/aks/blob/master/assets/KubeArchitecture.png)

### kubectl
Kubectl is command line interface for running commands against Kubernetes cluster.

### Building the docker image
`
 docker build . -t <imageName>:local
`

### To view all the docker images
`
 docker image list
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

## Deployment 

There are two ways we can do deployment of application in Kubernetes Cluster
- Interactively (via Kubectl)
- Using Declaration Manifest (YAML /JSON)

### To create deployment of the image via kubectl
`
kubectl run kubectl-deployment --image=letskube:local --port=80 --replicas=3
`

## Azure Container Registry
Azure Container Registry allows you to store images for all types of container deployments including DC/OS, Docker Swarm, Kubernetes, and Azure services such as App Service, Batch, Service Fabric, and others. Your DevOps team can manage the configuration of apps isolated from the configuration of the hosting environment.

### Steps to create ACR via Azure CLI

### 1. Create New Resource Group 
`az group create -n  letskube-rg -l westeurope`

### 2. Create ACR
`az acr create -n letskubedemo -g letskube-rg -l westeurope --sku Standard`

### 3. To show all the ACR list
`az acr list -o table`

If a default resource group is set, that's the resource group that will be used for `az acr list -o table`, then remove the default `az configure --defaults group=''`
