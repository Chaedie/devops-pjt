
### Configure IAM User for Terraform CLI

0. add permissions -> "AdministratorAccess" (for convenience on demo project)
1. create Access key 
2. `$ aws configure` 
3. input access key and secret key 
    - check `cat ~/.aws/credentials`
    - check `cat ~/.aws/config`
4. `terraform init` and more