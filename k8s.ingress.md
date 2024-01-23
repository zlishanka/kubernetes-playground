## Kubernetes ingress

### External service vs ingress
    - external req --> my-app ingress -->  my-app service --> my-app pod
    - ingress redirect the req to internal service "my-app"  

### ingress configuration
    Host: 
        - valid domain address
        - map domain name to Node's IP address, which is the entrypoint

### ingress controller - implementation of ingress
    - itself is a pod (ingress controller pod)
    - evaluates and processes ingress rules
    - manage redirections 
    - entrypoint to cluster
    - many third-party implementations
    - K8s Nginx ingress controller

### Environment on which your cluster runs
    - separate server
    - public IP address and open ports
    - cloud load balancer vs proxy server
    - entrypoint to cluster
    - No server in K8s cluster is accessible from outside

### Configure ingress in minikube
    - install ingress controller in minikube
```
        minikube addons enable ingress
```
    - automatically starts the K8s Nginx implementation of ingress contoller
```
        kubectl get pod -n kube-system
```


### check ingress 
    kubectl get ingress -n kubernetes-dashboard
 

### Multiple paths for same host (routing)
    - example: google domain has many services
    - in "Ingress" yaml file
    - http://myapp.com/analytics  --> analytics service --> analytics pod
                      /shopping   --> shopping service  --> shoppig pod

### Multiple sub-domains or domains
    - instead one host and multiple path, multiple hosts with one path 
    - multiple sub-domains
    - analytics.myapp.com,
    - shopping.myapp.com 
