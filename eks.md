aws login
aws configure

eksctl create cluster --config-file cluser.yaml

eksctl delete cluster -f cluster.yaml



eksctl create cluster --name=my-cluster --region=us-east-1 --node-type=t2.medium --nodes=2 --nodes-min=1 --nodes-max=3

eksctl delete cluster --name=my-cluster --region=us-east-1 --wait


## Links

https://docs.aws.amazon.com/eks/latest/eksctl/dry-run.html




