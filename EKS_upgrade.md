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
    --region us-east-1 \
    --nodegroup-name standard-workers \
    --node-type t3.medium \
    --nodes 3 \
    --nodes-min 2 \
    --nodes-max 4 \
    --managed


