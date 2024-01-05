1) Create IAM role for EKS Cluster.
2) Create dedicated VPC for the EKS Cluster.
3) Create EKS Cluster.
4) Install and setup IAM authenticator and kubectl utility.
5) Create IAM role for EKS worker node.
6) Create worker nodes.
7) Deploying demo application.

#### Install and setup IAM authenticator and kubectl utility:
````sh
Install kubectl on one test server.
aws eks --region ap-south-1 update-kubeconfig --name eks-cluster
more /home/ubuntu/.kube/config
export kUBECONFIG=~/.kube/config
kubectl get svc
 ````
#### Create IAM role for EKS worker node and Create worker nodes:
````sh
Create a role (w_role) with IAM policy: EKS_CNI_policy, EKSWorkerNodePolicy & EC2ContainerRegistryReadOnly
setup worker nodes on server:
EKS -> Compute (tab) -> add node group -> name (worker_node) -> Node IAM Role Name (choose above w_role)
````
URL: https://www.youtube.com/watch?v=aZd0UolVwD4
