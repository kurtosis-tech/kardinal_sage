# Kardinal Playground (AWS Demo)
AWS EKS clusters cost $0.10 per hour, so you may incur charges by running this tutorial. The cost should be a few dollars at most, but be sure to delete your infrastructure promptly to avoid additional charges. We are not responsible for any charges you may incur.

To delete all created resources, run: `terraform destroy`

## License
- The core of this playground was derived from [HashiCorp's EKS tutorial](https://github.com/hashicorp/learn-terraform-provision-eks-cluster), licensed under MPL 2.0. Referencing the [documentation](https://github.com/hashicorp/learn-terraform-provision-eks-cluster) for this library is advised.

## Prerequisites
- This repository features a devcontainer. To use it, install the Dev Containers VSCode extension (Microsoft)
- Clone this repository and open in VSCode

## Configuration
- By default, this repository deploys a cluster into `us-east-2`. In almost all cases, this is acceptable, but it can be changed via the `variables.tf` file in the root of the repository.

## Provision an EKS Cluster
Set up your AWS Credentials: 

- `aws configure` and follow the prompts.

Create infrastructure resources:

- `terraform init`
- `terraform apply` and wait. This step takes 5-10 minutes.

Configure kubectl: 

- `aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)`

Verify connection to EKS cluster:

- `kubectl cluster-info` should print out endpoints for the Kubernetes control plane and CoreDNS
- `kubectl get nodes` should return three worker nodes in the cluster

