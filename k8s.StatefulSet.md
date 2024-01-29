## StatefulSet 

    ### What is StatefuleSet?

        - K8s component used for stateful applications 
        - Database like MySQL, elasticSearch, mongoDB. Or app that stores data
        - Compared to stateless applications
        - Stateless apps deployed using Deployment, replicate your app
        - Stateful apps deployed using StatefulSet, replicate Pods
        - Both manage Pods based on container specification


    ### Deployment vs StatefulSet

        - replicating stateful apps is more difficult
        - cannot be created/deleted at the same time
        - can't be randomly addressed
        - replica Pods are not identical - Pod Identity (sticky identity for each pod)
        - Database synchronization is an example, master/slave, data consistency
        - Pod state, each pod has its own PV. So when Pod dies, Pod Id stored in PV can help recover. 
        - PV has to be remote storage 

    ### Pod identity 
        
        - Every pod has its own identifier
        - Deployment (random hash) 
        - StatefuleSet: fixed ordered names, $(statefulset name)-$(ordinal)
        - Next Pod is only created, if previous is up and running. 
        - Delete StatefulSet will be in reverse order, starting from last one created.
        - Own DNS Endpoint from Service

    ### Replicating stateful apps - Challenging tasks
    
        - Configuring the cloning and data synchronization
        - Make remote storge available

    
     
