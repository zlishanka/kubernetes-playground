# kubernetes-playground
Playground of Kubernetes

## Main K8s components 
### What is Pod
    - Smallest unit of K8s
    - Abastraction over container (only needs to interact with K8s layer)
    - Usually 1 application per Pod
    - Each pod gets its own IP address
    - New IP address on re-creation
     
### Service
    - permanent IP address
    - lifecycle of Pod and Service not connected
    - external/internal service 
    - serves as load balancer as well

### Ingress 
    - forward req to services
    - route traffic into cluster

### ConfigMap
    - external configuration of your application 
    
### Secrets
    - used to store secret data
    - base64 encoded
    - use it as environment vavriables or as properties file
        
### Volumes
    - store o local machine or remote storage, outside of K8s cluster
    - K8s doesn't manage data persistance

### Deployment 
    - blueprint for my-app Pods
    - end users create Deployments
    - abstraction of Pods
    - DB cannot be replicated via Depolyment

### StatefulSet
    - for stateful apps
    - like mongoDB, elastic search, MySQL, etc
    - Deployment of stateless Apps, StatefulSet for stateFul Apps or Databases
    - Deploying StatefulSet not easy
    - DB very often hosted outside of K8s cluster
    
## K8s Architecture
### Node - Woker machine in K8s cluster
    - each Node has multiple Pods on it
    - worker Nodes do the actual job
    - 3 processes must be installed on every Node
        - container runtime (like Docker)
        - Kubelet 
            - interacts with both container runtime and node 
            - starts the Pod with a container inside 
        - Kube Proxy
            - forward the reqs
            - intelligent forwarding logics inside
### Master processes
    - multiple masters exists in a K8s cluster 
        - API servers are load balanced
        - etcd are distributed storage across all masters 

    - 4 processes run on every master node
        - API server
            - cluster gateway, process update/query from client
            - acts as a gatekeeper for authentication
        - Scheduler 
            - schedule new Pod
            - intelligence to decide where to put the Pod
            - just decides on which Node new Pod should be scheduled, actually startup is done by kubelet
        - Controller Manager 
            - detects cluster state changes, like crashing/die of Pods
            - send req to Scheduler to restart failed Pods
        - etcd 
            - key Value store of cluster
            - cluster brain, cluster changes get stored in the key value store
            - Application data is not stored in etcd

             
### Example cluster set-up
    - 2 masters, 3 worker nodes (compared to worker nodes, master nodes consume less resources) 
    - Add new Master server/Node server
        (1) get new bare server
        (2) install all the master/worker node processes
        (3) add it to the cluster 

#### Minikube  
    - Production Cluster setup includes multiple master and work nodes 
    - Open source "Minikube" where Master and Node processes run on One machine 
    - docker container is preinstalled
    - on laptop or local machine, minicube creates Virtual Box 
    - node runs in that virtual box, 1 Node K8s cluster 
    - for testing purposes

####  Kubectl
    - command line tool for K8s cluster 
    - ways to connect Api Server - UI, API, CLI (kubectl) 
    - kubectl is the most powerful of 3 clients 
        - create/destroy pods 
        - create services
    - kubectl works for both minikube and actual cloud cluster 
     
             
