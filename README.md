# kubernetes_demo
Foobar is a Python library for dealing with word pluralization.

## Installation
Terraform dir has IAC for building EKS cluster with 2 worker nodes on AWS

Commands:
 - ```terraform init```
 - ```terraform plan```
 - ```terraform apply```

Kubernetes dir has templates yaml files to create the microservice and it's configs 

Commands:
- ```kubectl create -f kubernetes/```

application dir has dockerfile to dockerize the jar file

Commands:
- ```docker build -t registry/helloworld:latest```
- ```docker push registry/helloworld:latest```
 
Jenkinsfile for CI/CD, it build image ,push , then deploy to kubernetes 

## To be implemented
- jenkinsfile ci/cd pipline is not implemented in a good way for production, 
I would implement canary deployment with help of tools like istio and flagger.
- if we would have alot of microservices, I would use service mesh like istio for mutual tls between services,canary deployment...
- I would use Helm for having more dynamic templates and be able to create more enviromentes from kubernetes without copy/past for all temlates manytimes and change values 
