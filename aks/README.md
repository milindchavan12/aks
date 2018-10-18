# Azure Kubernetes Service
- AKS simplifies deployment, management and operations of kubernetes.
- Make it easy to deploy and manage Containerized applications without Container Orcherstration expertise.
- Eliminates the burden of on-going operations and maintenance by provisioning, upgrading and scaling resources on demand.
- Master node(s) are managed by Azure.

### Benefits of Azure Kubernetes Service
- Automated Kubernetes version upgrades and Patching. Microsoft manages the both patching and upgrades once released.
- Easy cluster scaling.
- Self healing hosted control plane (masters)

## Deployment of Application in Kubernetes cluster

There are two ways we can do deployment of application in Kubernetes Cluster
- Interactively (via Kubectl)
- Using Declaration Manifest (YAML /JSON)

### To create deployment of the image via kubectl
`
kubectl run kubectl-deployment --image=letskube:local --port=80 --replicas=3
`
