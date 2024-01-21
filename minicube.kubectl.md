# Installation and create minikube cluster 
## Sources

["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos)
["minikube"](https://minikube.sigs.k8s.io/docs/start/)	

## prerequisite
need to install either docker desktop or virtual box

## Install minikube 

```
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
    sudo install minikube-darwin-amd64 /usr/local/bin/minikube
``` 
   
    minikube has kubectl as dependency so NO need to install kubectl separately
    /usr/local/bin/minikube
    /usr/local/bin/kubectl

    minikube cli    - for start up/deleting the cluster 
    kubectl cli     - for configuring the minicube cluster 

## Start minikube 
```
minikube start
```
Creating docker container (CPUs=2, Memory=4000MB) ..	
Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...

Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
  	Enabled addons: storage-provisioner, default-storageclass
  	Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default

## Verify kubectl configuration
```
kubectl version --short
kubectl cluster-info		
kubectl cluster-info dump
```	

## Interact with your cluster
```
kubectl get po -A
```
    
## CRUD commands
    Deployment - abstraction over Pods
        - blueprint for creating pods
        - most basic configuration for deployment (name and image to use)
        - rest defaults 

    replicaset - managing the replicas of the pod 

    layers of abstraction 
        Deployment --> ReplicaSet --> Pod --> Container
        everything below deployment should be managed by K8s
 
    nginx-depl-6777bffb6f-kbfpt
        - deployment id: nginx-depl
        - replicaset id: 6777bffb6f
        - pod id: kbfpt

### create depployment
```
        kubectl create deployment nginx-depl --image=nginx
        kubectl create deployment mongo-depl --image=mongo
```
### edit the configuration of deployment 
```
        kubectl edit deployment nginx-depl
```
   
### delete the deployment
```
        kubectl delete deployment mongo-depl
```    
### apply deployment from configuration file
```
	kubectl apply -f nginx-deployment.yaml
```
     
## Status of different K8s components 
```
    kubectl get deployment
    kubectl get replicaset
    kubectl get pod
    kubectl describe pod nginx-deployment-86dcfdf4c6-2pv65
```
## Debugging pods
    
### get the pod log
```
	kubectl logs nginx-depl-6bdcdf7f5-5hp58
```
### get the pod terminal
```
        kubectl exec -it mongo-depl-558475c797-hp45d -- bin/bash	
```
