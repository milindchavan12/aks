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
So following things happens when we execute the above command:
- Deployment is created with desired state of 3 replicas.
- ReplicaSet are created which makes sure there are always 3 replicas are running.
- Scheduler then schdules the deployment on the Worker nodes
- Then instructs the docker engine running on worker node to pull the image and run on pods.

### To get deployment of the image via kubectl
`
kubectl get deployments
`

### To get replicasets of the image via kubectl
`
kubectl get rs
`

### To get pods of the image via kubectl
`
kubectl get pods
`
