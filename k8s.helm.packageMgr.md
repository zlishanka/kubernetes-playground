## K8s Helm - Package Manager of K8s

### What is Helm?
    - package manager for K8s. Like apt, yum, homebrew
    - to package Yaml files and distribute them in public/private repos
    - Helm charts
        - bundle of yaml files
        - create your own helm charts with helm
        - push them to Helm Respository
        - download and use existing ones
        - DB apps (mongo, elasticsearch, mysql), Monitoring apps, promotheus have heml charts avaiable, reuse

    - helm search <keyword> 
    - public/private regsitries

### Templating Engine
    - Template Yaml config
        apiVersion: v1
        kind: Pod
        metadata:
          name: {{.Values.name}}
        spec:
          containers:
          - name: {{.Values.container.name}}
            image: {{.Value.container.image}}
            port: {{.Value.container.port}}
 
    - values.yaml 
        name: my-app
        container:
            name: my-app-container
            image: my-app-image
            port:9001
        
### Sample applications across different environments
    - Dev, staging, production

### Helm Chart Structure
    - mychart/
        chart.yaml
        values.yaml
        charts/
        templates/

    helm install <chartname>
    
    - Template files will be filled with the values from values.yaml
    - helm install --values=my-values.yaml <chartname>

### Release management 
    helm install <chartname>
    helm upgrade <chartname>
    helm rollback <chartname> 
 
 
