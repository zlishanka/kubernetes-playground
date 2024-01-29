## K8s Volumes 

### How to persist data in Kubernetes using Volumes. 

	- Persistent Volume, Persistent Volume Claim, Storage Class 
	- Storage that doesn't depend on the pod lifecycle. 
	- Storage must be available on all nodes.
	- Storage needs to survive even if cluster crashes. 
	- Another use case is to write/reads session data

### Persistent Volume 

	- cluster resource
	- created via Yaml file
		 apiVersion: v1
		 kind: PersistentVolume
		 metadata:
		   name: 
		 spec:
		   capacity 

	- needs actual physical storage, like local disk, nfs server, or cloud storage
	- Where does this storage come from and who makes it available to the cluster?
	- What type of storage do you need?
	- external plugin to your cluster

	- Pesistent volume outside of the namespaces, accessible to the whole cluster
	- local vs. Remote volume types 

### Who creates Persistent Volume and when

	- Storage resources is provisioned by Admin
	- Create the PV components from storage backends
	- Application has to claim the Persistent Volume (PVC)
		kind: PersistentVolumeClaim
	- Use PVC in the Pods configuration
		apiVersion: v1 
		kind: Pod
		metadata: 
 		  name: mypod
		spec:
		  containers:
            - names: myfrontend
              image: nginx
		  volumes:
		  - name
		  	persistentVolumeClaim:
	- Claims must be in the same namespace! 
	- Volume is mounted into the Pod
	- Volume is mounted into Container

### ConfigMap and Secret
	- local volume
	- not created via PV and PVC
	- managed by Kubernetes
	

### Storage class 
	apiVersion: storage.k8s.io/v1
	kind: StorageClass
	metadata: 

			

