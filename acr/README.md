
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