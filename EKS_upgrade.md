eksctl create cluster 


eksctl create cluster \
    --name <cluster-name> \
    --region <region> \
    --nodegroup-name <nodegroup-name> \
    --node-type <instance-type> \
    --nodes <number-of-nodes> \
    --nodes-min <min-nodes> \
    --nodes-max <max-nodes> \

Example :


eksctl create cluster \
    --name my-eks-cluster \
    -- version 1.28 \
    --region us-east-1 \
    --nodegroup-name standard-workers \
    --node-type t3.medium \
    --nodes 2 \
    --nodes-min 2 \
    --nodes-max 4 \
    --managed

Optional Flags

--version: Specify Kubernetes version (e.g., --version 1.29).
--vpc-private-subnets / --vpc-public-subnets: For custom networking.
--ssh-access and --ssh-public-key: Enable SSH access to nodes.


https://github.com/javahometech/pyapp-eks-deploy

kubectl apply -f ./   # ./ will picks all files in current folder 

UPGRADE PROCESS:

1. First upgrade control plane
2. Second ADDON shuld be upgrade
3. Finally NODEGROUP could be upgraded
   
CLUSTER UPGRADE COMMAND 
1. First upgrade control plane
eksctl upgrade cluster --name my-eks-cluster --region us-east-1 --version 1.29 --approve

2. Second ADDON shuld be upgrade

   eksctl update addon --cluster my-eks-cluster --region  us-east-1 --name kube-proxy --force
   eksctl update addon --cluster my-eks-cluster --region  us-east-1 --name coredns --force
   eksctl update addon --cluster my-eks-cluster --region  us-east-1 --name vpc-cni --force\

   Get status:
        eksctl get addons --cluster my-eks-cluster --region us-east-1
   
4. Finally NODEGROUP could be upgraded

   aws eks update-nodegroup-version --cluster-name my-eks-cluster --region us-east-1 --nodegroup-name standard-workers --kubenetes-version 1.29

   
   





