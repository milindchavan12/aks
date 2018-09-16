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

### To create deployment of the image
`
kubectl run kubectl-deployment --image=letskube:local --port=80 --replicas=3
`
