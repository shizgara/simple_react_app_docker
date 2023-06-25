# Task:
### - Install Tekton in Kubernetes cluster.
### - Using Tekton please create pipeline to build and deploy NodeJS React application

---

## Preparing environment

#### In my case I use EC2 instance on AWS c4.xlarge(for better performance) with Ubuntu 20.04:latest and 10 Gb storage. I use minikube as local Kubernetes

#### 1. Install necessary tools

#### - [Install minikube](https://minikube.sigs.k8s.io/docs/start/)
#### - [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
#### - [Install Tekton CLI](https://tekton.dev/docs/cli/)
#### - [Install Docker](https://docs.docker.com/engine/install/ubuntu/)

#### 2. Additional configuration

#### - sudo usermod -aG docker $USER   - ***add your user to the Docker group***

#### - sudo reboot - ***apply new syste, configuration***

#### - minikube start - ***run minikube ***















## Part 1 (Install Tekton in Kubernetes cluster)

#### 1-2. I have downloaded and installed  MySQL server on VM

![1-2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/1.PNG)

#### 3-4. I have selected and created a database on the server through the console

![3-4](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/4.PNG)

#### 5. I have filled in tables

![5.1](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/5_1.PNG)
![5.2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/5_2.PNG)
![5.3](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/5_3.PNG)

#### 6. I have constructed and executed SELECT operator with WHERE, GROUP BY and ORDER BY

![6](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/6.PNG)

#### 7. I executed other different SQL queries DDL, DML, DCL

![7.2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/7_1.PNG)
![7.2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/7_2.PNG)

#### 8. I created a database of new users with different privileges

![8.1](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/8_1.PNG)
![8.2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/8_2.PNG)
![8.3](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/8_3.PNG)
![8.4](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/8_4.PNG)

#### 9. I made a selection from the main table DB MySQL.

![9](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%201/9.PNG)



## Part 2

#### 10-11. I have made backup of my database and then deleted the table

![10-11](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/10-11.PNG)

#### 12. I have restored my database

![12](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/12.PNG)

#### 13-14. I have transfered my local database to RDS AWS and connected to my database

![13-14.1](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/13_14_1.PNG)
![13-14.2](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/13_14_2.PNG)

#### 15. I have executed SELECT operator

![15](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/15.PNG)

#### 16. I executed other different SQL queries DDL, DML, DCL

![16](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%202/16.PNG)



## Part 3 (MongoDB)

#### 17-19 I have created a database.  After that i used the use command to connect to a new database. Then I have created a collection. I have used db.createCollection to create a collection. I have created some documents. Inserted a couple of documents into my collection

![17-19](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%203/7_3_1.PNG)

#### 20. I have  used find() to list documents out.

![20](https://github.com/shizgara/DevOps_online_Rivne_2022Q1Q2/blob/master/m7/img/part%203/7_3_2.PNG)

