# Task:
### - Install Tekton in Kubernetes cluster.
### - Using Tekton please create pipeline to build and deploy NodeJS React application


---


## Preparing environment

#### In my case I use EC2 instance on AWS c4.xlarge(for better performance) with Ubuntu 20.04:latest and 10 Gb storage. I use minikube as local Kubernetes

#### 1. Install necessary tools

####     - [Install minikube](https://minikube.sigs.k8s.io/docs/start/)
####     - [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
####     - [Install Tekton CLI](https://tekton.dev/docs/cli/)
####     - [Install Docker](https://docs.docker.com/engine/install/ubuntu/)

#### 2. Additional configuration

`sudo usermod -aG docker $USER`   - **add your user to the Docker group**

`sudo reboot` - **apply(update) new system configuration**

`minikube start` - **run minikube**


---


## Install Tekton in Kubernetes cluster and dependencies

 `kubectl apply --filename https://storage.googleapis.com/tekton-releases/pipeline/latest/release.yaml` - **install Tekton**

 `tkn hub install task kaniko && tkn hub install task git-clone && tkn hub install task kubernetes-actions` - ___install tasks from Tekton Hub___


 ---


## Clone repository with manifest, sources and Tekton files

`git clone https://github.com/shizgara/simple_react_app_docker.git` - **clone repository to local instance**

`cd simple_react_app_docker/tekton\ pipeline/` - **move to tekton files**


---


## Generate and apply credentials for Docker

`docker login` – **you have to make docker login to generate  /home/shizgara/.docker/config.json**  
Enter username and password to DockerHub. When it done, you will see

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/docker%20login.PNG)

After that you have to make secret for docker credentials. And run the output file  
`kubectl create secret generic docker-credentials --from-file=/home/$USER/.docker/config.json --dry-run=client --output=yaml > docker-credentials.yaml` - **make docker-credentials.yaml**

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/docker-credentials.png)

`kubectl apply -f docker-credentials.yaml` – **run credentials**   
**You can check it** – `kubectl get secret`

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/kubectl%20get%20secret.PNG)


---


## Run pipeline

You must be in **~/simple_react_app_docker/tekton pipeline**. Here we have few files, which to runs our pipeline.
Firstly we create the service account, which allow provides an identity for processes that run in a Pods. Here is the content of service-account.yaml  
 ![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/service%20account%20yaml.PNG)

#### Run service-account.yaml and check it  
`kubectl apply -f service-account.yaml`

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/kubectl%20get%20service%20account.PNG)

#### Secondly we run role.yaml, which create role and bind it with service account created in previous step

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/role%20yaml.PNG)

`kubectl apply -f role.yaml`

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/kubectl%20get%20role.PNG)

#### After that we can apply pipeline with tasks and run it with pipelinerun

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/pipiline1.PNG)
![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/pipiline2.PNG)
![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/pipilinerun.PNG)

`kubectl apply -f pipeline.yaml` - **run pipeline**  
`kubectl create -f pipelinerun.yaml` - **run pipelinerun**

#### We can see the logs of pipelinerun

`tkn pipelinerun logs <name created pipilinerun> -f`

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/log1.PNG)
![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/log2.PNG)
![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/log3.PNG)

`kubectl get pods –watch`

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/get%20pods.PNG)

#### Now we check our app. Does it run?

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/check%20arun%20app.PNG)


---


#### Dockerfile for image creation

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/dockerfile.PNG)

#### Manifest file, for deployment  

Here we run 2 pods with our app. App running on port 3000. So Load balancer map tcp requests from 80 to 3000 port

![](https://github.com/shizgara/simple_react_app_docker/blob/main/screenshots/manifest.PNG)


---


## Links
https://tekton.dev/docs/getting-started/tasks/  
https://adamtheautomator.com/tekton-kubernetes/  
https://earthly.dev/blog/building-k8s-tekton/  
https://developer.ibm.com/tutorials/build-and-deploy-a-docker-image-on-kubernetes-using-tekton-pipelines/  
https://hub.tekton.dev/  
https://github.com/tektoncd/cli/blob/main/README.md  
