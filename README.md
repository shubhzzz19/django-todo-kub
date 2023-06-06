# django-todo kubernetes cluster project
A simple todo app built with django

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
minikube start --driver=docker
```
