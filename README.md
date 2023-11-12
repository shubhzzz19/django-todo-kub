# Django TODO Kubernetes Cluster Project

1. Built Kubernetes Cluster on AWS from Scratch with Minikube.
2. Setup and managed docker containers for Django and React Application into Kubernetes Pods.
3. Managed deployment, replication, auto-healing, auto-scaling for Kubernetes Cluster.
4. Managed network and services with host IP allocation through proxy on AWS EC2 and Route53.

*Achievements: Reducted downtime by 75% on Production Environment.*

## Step 1 : Create a AWS Linux 2 (t2.medium) instance and allocate the Elastic IP to the instance

For Docker Installation
```
sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER && newgrp docker
sudo systemctl enable docker
sudo systemctl start docker
```
For Kubernetes
```
sudo tee /etc/yum.repos.d/kubernetes.repo <<EOF
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg
        https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
```
```
sudo yum install -y kubectl kubeadm kubelet
sudo systemctl enable kubelet
sudo systemctl start kubelet
```

For Minikube & Kubectl
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube 
minikube start --driver=docker --force
```

## Step 2 : Clone the repo and go to k8s directory to start the pods
```
git clone https://github.com/shubhzzz19/django-todo-kub.git
cd django-todo-kub
```

## Step 3 : Run the Kubernetes files
```
kubectl apply -f pod.yaml
kubectl apply -f deploy.yaml
kubectl apply -f service.yaml
```

## Step 4 : Managed network and services with host Ip allocation
```
minikube service <service name> --url
```
You will get the IP ,then copy the IP and edit the hosts file
```vi /etc/hosts```
Insert the below in the /etc/hosts
```<ip> todo-app.com```

## Step 5 : Now curl the App with name given in the hosts 
```curl -L http://todo-app:30007```

As you can see the output of the curl our app is running 💥
