# Kubernetes configuration file 
    yaml configuration file (human friendly, strict indent) 
    contains 3 major parts, metadata, spec status
    storage the configuration with code (infrastruture as code) 

## kind
    either Deployment or  Service
## metadata
    name, labels
## specification (spec)
### replicas
### template
    has its own metadata
        apply to pod
    has its own spec
        blueprint for pod (name, port, image...)
   
    selector: matchlabel im metadata's label, pod gets label thru template blueprint
 
 
## status 
    desired state ?? == actual state ??
    
### where does K8s get the statue update 
    etcd - cluster change gets saved in key-value store
        - hold the current status of any K8s components
 
