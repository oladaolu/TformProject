# Project Overview
I have used terraform as an Infrastructure as code (IaC) tool to provision my infrasctructure on AWS. Provisioned infrastructure inlude;
VPCs, EKS Clusters, Private and Public subnets, Iinternet Gateway, Routing Tables, SECURITY GROUP, etc.
https://github.com/oladaolu/TformProject/blob/master/CI-CD%20Intergration.JPG

# EKS Getting Started Guide Configuration

This is the full configuration from https://www.terraform.io/docs/providers/aws/guides/eks-getting-started.html

See that guide for additional information.

NOTE: This full configuration utilizes the [Terraform http provider](https://www.terraform.io/docs/providers/http/index.html) to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes servers. 

# Provision EKS Infrastructure on AWS using Terraform
To provision the EKS infrastructure on AWS, I followed the guidelines provided in the EKS Getting Started Guide. This comprehensive guide helped me configure the necessary components for creating and managing an EKS cluster. By following the steps outlined in the guide, I successfully set up and deployed an EKS cluster, enabling efficient orchestration and management of containerized applications

terraform init
terraform plan
terraform apply
terraform destory

# Jenkins Continuous Integration and Deployment
To achieve continuous integration and continuous deployment (CI/CD), I utilized Jenkins as the automation server. I implemented a Jenkins pipeline script that automated various stages of the software delivery process. This included building the application using Maven, performing automated tests using Selenium, validating the code quality using SonarQube, and uploading the build artifacts to a Nexus private artifact repository. Jenkins enabled streamlined and efficient CI/CD workflows, ensuring that applications were built, tested, and deployed seamlessly.
Jenkins will enable us to achieve Continuos Integration and Continuous Deployment. Our Jenkins pipeline-script  will ensure once the application is developed or modified it is automatically build using maven, tested using selenium, validated using SonarQube. The build artifacts will be uploaded to Nexus Private aritifact repository. 
# GitHub
The source code and scripts for this project are stored in a GitHub repository. You can access the repository at https://github.com/WinifredZenabuin/UnityProject. To enable automated builds triggered by source code modifications, I configured GitHub webhooks. This integration allowed Jenkins to automatically initiate a build processwhenever changes were pushed to the repository, ensuring a seamless development and deployment workflow.  

# Dockerfile
For containerization of the application, I leveraged Docker, a popular containerization tool. Using the provided Dockerfile, I created a Docker image that encapsulatedthe application code and its dependencies. This containerized approach allowed for consistent and portable deployment of the application, ensuring that it could run reliably across different environments. With Docker, I achieved efficient and isolated application deployments, simplifying the management and scalability of the application. We are also using the created package (artifacts) to create a docker imgae for our application. Here docker is used for containerisation.  
```docker
docker build -t legah2045/springboot-app .
```
# Kubernetes Manifest files
This files will deploy a "Spring-boot-app" with a MongoDB. Our application and database is deployed using Replicat Set, ConFigMap, Ingress Controller, Secrets, PVC, StorageClass, HPA, and Cluster-Auto-Scaling.
We have also deployed Grafana and Prometheus using Helm Charts. This will monitor our applications, send alerts and as such we are going to achieve high availability.
```t
kubectl create deployment autoscaler-demo --image=nginx
kubectl get pods --all-namespaces | grep Running | wc -l
kubectl get nodes -o yaml | grep pods
kubectl scale deployment autoscaler-demo --replicas=20
```

# Build Project Using Maven

Maven is java based build tool to generate executable 

packages(jar, ear,war) for java based projects.

```bash
mvn clean package
```

## Create Docker Image
Docker is a continerization tool.Using docker we can deploy our applications as 

containers using docker images. Containers contains application code and also the softwares,

config files whatever is required for our application to run.

Create docker image using Dockerfile


```docker
docker build -t legah2045/springboot-app .
```

## Deploy Application Using EKS Cluster 

```kubectl apply 
kubectl apply -f springboot-app-deployment.yml
```

## List Docker Containers
```docker
docker ps -a
```

## License
[Winifred Zenabuin](https://www.linkedin.com/in/winifred-zenabuin-1b430b194/)
