## Demo project to create MongoDB and Mongo Express services using K8s

### Overiew of K8s components
    Internal Service - MongoDB (pod)
    ConfigMap -DB Url
    Secret - DB User, DB Pwd
    Deployment.yaml - Env variables
    External Service - Mongo Express (pod) 

    2 Deployment/Pod
    2 Service
    1 ConfigMap
    1 Secret

    URL:
        - IP address of Node
        - Port of external Service 

    Browser req --> Mongo Express external service --> Mongo Express (pod) --> MongoDB internal Service --> MongoDB (pod)
    
###  deployment.yaml file 
```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: mongodb-deployment
      labels:
        app: mongodb
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: mongodb
      template:
        metadata:
          labels:
            app: mongodb
        spec:
          containers:
          - name: mongodb
            image: mongo
            ports:
            - containerPort: 27017
            env:
            - name: MONGO_INITDB_ROOT_USERNAME
              value: 
            - name: MONGO_INITDB_ROOT_PASSWORD
              value: 
```
     
### environment variables,  check on mongo docker image online

  mongodb:  
    MONGO_INITDB_ROOT_USERNAME, 
    MONGO_INITDB_ROOT_PASSWORD
    port - 27017

    echo -n 'username' | base64
    echo -n 'password' | base64

  mongodb-express:
    ME_CONFIG_MONGODB_ADMINUSERNAME
    ME_CONFIG_MONGODB_ADMINPASSWORD
    ME_CONFIG_MONGODB_SERVER
    port: 8081

### Secret creation, mongo-secret.yaml (example, no secret here at all)

```
    apiVersion: v1
    kind: Secret
    metadata:
        name: mongodb-secret
    type: Opaque
    data:
        mongo-root-username: dXNlcm5hbWU=
        mongo-root-password: cGFzc3dvcmQ=
```
