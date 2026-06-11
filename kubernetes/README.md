# Setting of EKS cluster

## Creating Role
*EKSClusterRole*
   To enable control plane to talk to different aws services 
Service: EKS Cluster
Policy: AmazonEKSClusterPolicy,AmazonEKSVPCResourceController

*NodeGroupRole* 
   For worker nodes the data plane so that they can talk to control plane,pull ECR images etc
Service: EC2
AmazonEKSWorkerNodePolicy,AmazonEC2ContainerRegistryReadOnly,AmazonEKS_CNI_Policy,AmazonSSMManagedInstanceCore 
AmazonEKSWorkerNodePolicy — lets nodes connect to the cluster
AmazonEC2ContainerRegistryReadOnly — lets nodes pull container images from ECR
AmazonEKS_CNI_Policy — lets the VPC CNI plugin manage pod networking (assign IPs to pods)


# Create cluster 

 select EKSClusterRole for the cluster 
 Once cluster has created go to compute tab and  create node group for dataPlan and  give role NodeGroupRole


 Local Setup 
 1. install AWS CLI and run aws configure command 
 2. install  kubectl  
 3. update kubectl config file 
 update-kubeconfig --region <aws Region name> --name <EKS cluster name>
Ex : update-kubeconfig --region us-east-1 --name MyFirstEKSCluster
validate with running the following commnds 

4. kubectl get pods -A (lis out the pods )

5. create a namespace for your project 
   kubectl create namespace dev
6. create a spring boot project    

