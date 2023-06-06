# django-todo kubernetes cluster project
A simple todo app built with django

## Step 1 : Create a AWS Linux 2 (t2.medium) instance and allocate the Elastic IP to the instance

For Docker Installation
'''
sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER && newgrp docker
'''

For Minikube & Kubectl
'''
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube 
minikube start --driver=docker
'''
