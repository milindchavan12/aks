# Azure Kubernetes Service
- AKS simplifies deployment, management and operations of kubernetes.
- Make it easy to deploy and manage Containerized applications without Container Orcherstration expertise.
- Eliminates the burden of on-going operations and maintenance by provisioning, upgrading and scaling resources on demand.
- Master node(s) are managed by Azure.

### Benefits of Azure Kubernetes Service
- Automated Kubernetes version upgrades and Patching. Microsoft manages the both patching and upgrades once released.
- Easy cluster scaling.
- Self healing hosted control plane (masters)

## Deployment of Application in Kubernetes cluster [Local]

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

### To get replicasets via kubectl
`
kubectl get rs
`

### To get pods via kubectl
`
kubectl get pods
`

### To create service via kubectl
The Service of type NodePort exposes the service on each nodes IP

`
kubectl expose deployment letskube-deployment --type=NodePort
`

### To verifiy if the service is created
`
kubectl get svc
`

### To delete the local deployment and service
`
kubectl delete deployment kubectl-deployment

kubectl delete service kubectl-deployment
`

### To create deployment of the image via YML file 
`
kubectl create -f .\letskubedeploy.yml
`

### To update deployment of the image with new version 
`
kubectl set image deployment letskube-deployment letskube=letskubeacr.azurecr.io/letskube:v2
`

------------------------------------------

## Service Principal
AKS uses the Service Principal to access the other Azure Resources like the Azure Container Registry (ACR)

### To create Service Principal via Azure CLI
`az ad sp create-for-rbac --skip-assignment`

### Get ACR ID
`az acr show --name letskubeacr --resource-group letskuberg --query "id" --output tsv`

### Grant the role assignment
`az role assignement create --assignee <appId-from-ad> --role Reader --role $acrId`

-------------------------------------------

# Create Azure Kubernetes Service Cluster

`az aks create
        --name letskubecluster 
        --resource-group letskuberg  
        --node-count 1       
        --generate-ssh-keys
        --service-principal <app-id>
        --client-secret <app-secret>
`

### Get AKS cluster credentials
`az aks get-credentials --name letskubecluster --resource-group letskubecrg`
