### Demo project accompanying a [Consul crash course video](https://www.youtube.com/watch?v=s3I1kKKfjtQ) on YouTube


Terraform commands to execute the script

```sh
# initialise project & download providers
terraform init

# preview what will be created with apply & see if any errors
terraform plan

# exeucute with preview
terraform apply -var-file terraform.tfvars

# execute without preview
terraform apply -var-file terraform.tfvars -auto-approve

# destroy everything
terraform destroy

# show resources and components from current state
terraform state list
```

#### Get access to EKS cluster
```sh
# install and configure awscli with access creds
aws configure

# check existing clusters list
aws eks list-clusters --region eu-central-1 --output table --query 'clusters'

# check config of specific cluster - VPC config shows whether public access enabled on cluster API endpoint
aws eks describe-cluster --region eu-central-1 --name myapp-eks-cluster --query 'cluster.resourcesVpcConfig'

# create kubeconfig file for cluster in ~/.kube
aws eks update-kubeconfig --region eu-central-1 --name myapp-eks-cluster

# test configuration
kubectl get svc
```

#### helm consul
```sh
# helm with eks
helm install eks hashicorp/consul --version 1.0.0 --values consul-values.yaml --set global.datacenter=eks

# helm with lke
helm install lke hashicorp/consul --version 1.0.0 --values consul-values.yaml --set global.datacenter=lke

```

### Commands to check the kubectl service, pods, all
``` sh
# test configuration
kubectl get svc
# test pod
kubectl get pod
# test node
kubectl get node
# get all
kubectl get all
```

