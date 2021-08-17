# EKS Clusters Terraform creation with Jenkins Pipeline

Allow SUDO permissions for Jenkins User:
----------------------------------------
 visudo
Add below line inside the file and save it
 jenkins ALL=(ALL)       NOPASSWD: ALL
 
Make PasswordAuthentication to yes:
-----------------------------------
 vi /etc/ssh/sshd_config
Change PasswordAuthentication value from no to yes
Restart sshd service:
 service sshd restart
Download 1.14.6 version of kubectl and aws-iam-authenticator

https://docs.aws.amazon.com/eks/lates...
https://docs.aws.amazon.com/eks/lates...


Plugins:
----------
 Pipeline: AWS steps
 Terraform
Get Pipeline code from here:
https://github.com/ejazzazeem/eks_cluster_jenkins_pipeline/blob/main/Jenkinsfile

Manual Testing:
----------

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
