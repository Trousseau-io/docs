
Trousseau installation deploys and maintains its component as container using native Kubernetes API and mechanism along with the standard KMS (Key Management Service) tooling.   

In production-grade environment, a *separation of duties* will most likely be in place dividing the work between a DevOps team in charge of the Kubernetes side while a Security team will be in charge of the KMS one. The installation guide will mention who is doing what with ***Platform team*** and ***Security team*** mark. 

The following workflow shows the installation steps and owners:

| # | Activity |Responsible Team|
|---|----------|----------------|
| 1 | [Create a Kubernetes ServicesAccount](#create-a-kubernetes-serviceaccount-kubernetes-admins) | ***Platform Team***|
| 2 | [HashiCorp Vault Kubernetes Authentication & Transit engine](#hashicorp-vault-kubernetes-authentication--transit-engine-kubernetes-admins--security-admins) | ***Platform Team*** <br> ***Security Team***|
| 3 | [Create a Trousseau Kubernetes ConfigMap](#create-a-trousseau-kubernetes-configmap-kubernetes-admins) | ***Platform Team***|
| 4 | [Deploy the Trousseau DaemonSet](#deploy-trousseau-daemonset-kubernetes-admins) | ***Platform Team***|
| 5 | [Enable Trousseau KMS provider in ```kube-apiserver```](#enable-trousseau-kms-provider-in-kube-apiserver-kubernetes-admins)| ***Platform Team***|
| 6 | [Create and verify Secret encryption with Trousseau and HashiCorp Vault](#create-and-verify-secret-encryption-with-trousseau-and-hashicorp-vault-kubernetes-admins) | ***Platform Team*** | 
| 7 | [Replace existing Kubernetes secrets with encrypted ones using Trousseau](#replace-existing-kubernetes-secrets-with-encrypted-ones-using-trousseau-kubernetes-admins) | ***Platform Team***|