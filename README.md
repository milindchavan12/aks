# AKS : Azure Kubernetes Service

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications." - Primary definition from https://kubernetes.io/

- Kubernetes exposes the underlying infrastructure as a singel conputational resource.
- Consistent deployment exprience regardless of the size og the cluster.

![img text](https://github.com/milindchavan12/aks/blob/master/assets/KubeArchitecture.png)

### kubectl
Kubectl is command line interface for running commands against Kubernetes cluster.

## Building the docker image
`
 docker build . -t <imageName>:local
`
