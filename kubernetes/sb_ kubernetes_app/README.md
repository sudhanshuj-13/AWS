# Setting of EKS cluster

## Creating Role
EKSClusterRole   - To enable control plane to talk to different aws services 
 Service: EKS Cluster
Policy: AmazonEKSClusterPolicy,AmazonEKSVPCResourceController

NodeGroupRole -- For worker nodes the data plane so that they can talk to control plane,pull ECR images etc
Service: EC2
AmazonEKSWorkerNodePolicy,AmazonEC2ContainerRegistryReadOnly,AmazonEKS_CNI_Policy,AmazonSSMManagedInstanceCore 
AmazonEKSWorkerNodePolicy — lets nodes connect to the cluster
AmazonEC2ContainerRegistryReadOnly — lets nodes pull container images from ECR
AmazonEKS_CNI_Policy — lets the VPC CNI plugin manage pod networking (assign IPs to pods)