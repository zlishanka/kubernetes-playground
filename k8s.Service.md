## K8s Services

    ### What is K8s services
   
        - Each Pod has its own IP address, Pod can die anytime, it's not feasible to access pod thru IP addr.
        - Service 
            - Stable IP address to access Pod
            - loadbalancing 
            - loose coupling
            - within & outside cluster 

         
    ### Different types of Services

        - ClusterIP Services
            - IP Address from Node's range
            - kubectl get pod -o wide 
            - req --> Ingress --> Service (port 3200) --> Pod
            - selector, service uses selector to decide which Pod to forward req
                - Kind: Service
                  metadata:
                    name: microservie-one-servie
                  spec:
                    selector:
                      app: microservice-one
            - Pods are identified via "Selectors", key value pairs, labels of Pods

            - Service:
                selector:

            - Deployment of Pod
                labels:
                  app:

            - Multiple port services 
        
        - Headless Services
            - DNS lookup 
            - Set clusterIP to "None", returns Pod IP address instead
            - Userful for Stateful application 
            

        - Service type attributes 
            - ClusterIP
            - NodePort: range 30000-32767
            - LoadBalancer

        - LoadBalancer
            - extension of NodePort Service
            - NodePort Service is an extension of CluterIP service
    ### How to use services 

            
