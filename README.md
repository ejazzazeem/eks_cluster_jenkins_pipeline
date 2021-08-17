# clusters Terraform creation

You can provision multiple EKS clusters with a single `terraform apply`:

```bash
terraform init
terraform plan
terraform apply
```

It might take a while for the cluster to be creates (up to 15-20 minutes).

At the end you will have:

1. A cluster for development.
1. A cluster for staging.
1. A cluster for production.

In the same folder you will find a kubeconfig file for each cluster.

NOTE: This full configuration utilizes the Terraform http provider to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes master servers. Feel free to replace this as necessary.
