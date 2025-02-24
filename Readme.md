# DevOps Project

## 0. Configure IAM User for Terraform CLI

0. add permissions -> "AdministratorAccess" (for convenience on demo project)
1. create Access key 
2. `$ aws configure` 
3. input access key and secret key 
    - check `cat ~/.aws/credentials`
    - check `cat ~/.aws/config`

## 1. VPC

```
📦terraform
 ┣ 📜0-locals.tf
 ┣ 📜1-providers.tf
 ┣ 📜2-vpc.tf
 ┣ 📜3-igw.tf
 ┣ 📜4-subnets.tf
 ┣ 📜5-nat.tf
 ┗ 📜6-routes.tf
``` 

- 1 IGW
- 2 Public Subnet (AZ A, B)
  - 1 NAT Gateway 
- 2 Private Subnet (AZ A, B)


## 2. EKS

```
📦terraform
 ┣ 📜7-eks.tf
 ┗ 📜8-nodes.tf
```


- EKS (Managed by AWS)
- Nodes (Managed by AWS)

```bash
$ aws eks update-kubeconfig --region ap-northeast-2 --name staging-demo # kubectl to eks
$ kubectl get nodes
$ kubectl auth can-i "*" "*"
```