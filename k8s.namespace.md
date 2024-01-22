## Namespace of K8s

### What is namespace?

    - organize resources in namespaces
    - Virtual cluster inside a cluster
    - use cases 
        (1) resources (deployment, pod, configMap..) are grouped in namespaces
        (2) In cases, many teams, same application
        (3) Resource sharing: staging, development, re-use thoese components in both environments 
        (4) Production version: blue, green, etc re-use thoese components in both environments
        (5) different project has its own namespace, Project A, Project B, so each has its own isolated environment and limited resources

    - 4 namespaces by default 
        default                Active   2d1h
        kube-node-lease        Active   2d1h
        kube-public            Active   2d1h
        kube-system            Active   2d1h
        kubernetes-dashboard   Active   2d1h

### kubernetes-dashboard
    - only with minikube 

### kube-system 
    - Do NOT create or modify in kube-system
    - System processes
    - Master and kubectl processes

### kube-public
    - publicly accessible data
    - A configmap, which contains cluster information

### kube-node-lease
    - heartbeats of nodes
    - each node has associated lease object in namespace
    - determines the availability of a node

### default 
    - resources you create are located here 

### Create a namespace
    kubectl create namespace my-namespace

### Examples to use namspace 
    - Database, Monitoring, Elastic stack, Nginx-ingress 

### Characteristics of namespace
    - Each NS must define own ConfigMap, Secret
    - you can't access most resources from another namespace
    - you can access Service in another Namespace
    - components like Volume, node are live globally, cannot be isolated

### create component in a defined namespace
    kubectl apply -f mongo-service.yaml --namespace=my-name
    or 
    inside configration file
```
    metadata:
      name: mysql-configmap
      namespace: my-namespace
``` 
    change active namespace (brew install kubectx) 
```
    kubens my-namespace
```  
