node -v
npm init -y
npm install express
node .

## check if the app is working locally on the browser
localhost:3000



## INSTALLATION OF KUBERNETES AWS EKS 

1. first install the aws cli on an EC2 instance
## install aws cli
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" 
sudo apt install unzip 
unzip awscliv2.zip 
sudo ./aws/install

#check the version

aws --version
2. then create IAM user with adminAcess in AWS with  access key and secret key generated
Run aws configure
Authenticate with the command below
aws sts get-caller-identity
aws s3 ls

3. install kubectl on local machine and confirmed installation by running the command
### Install Kubernetes Kubectl:

    curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
    kubectl version 
kubectl version --client

4. ## install eksctl

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

eksctl version

5. Create AWS EKS cluster

## Pre-requisite links
https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

6. ## Create EKS cluster
eksctl create cluster --name eks-cluster-201 --node-type t3.medium --nodes 1 --nodes-min 1 --nodes-max 2 --region eu-north-1

## Get cluster now
eksctl get cluster 

## Get EKS Cluster service
eksctl get cluster --name eks-cluster-201 --region eu-north-1

## Get EKS Pod data.
kubectl get pods --all-namespaces

## To update kubernetes config file
aws eks update-kubeconfig --name eks-cluster-201

kubectl get nodes

kubectl apply -f deployment.yaml

kubectl get pods

kubectl describe pod nginx-deployment-77d8468669-dd9d4

kubectl get svcsx

7. ## Delete EKS cluster
eksctl delete cluster --name eks-cluster-201 --region eu-north-1
##or 
eksctl delete cluster --region=eu-north-1 --name=eks-cluster-201



