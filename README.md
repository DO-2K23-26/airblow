# Airflow X ArgoCD

## Prérequis

- Avoir un cluster kubernetes
- Installer helm

## Installation de ArgoCD

Pour installer ArgoCD il suffit de lancer les commandes suivantes :

``` bash
kubectl create namespace argocd
helm repo add argo https://argoproj.github.io/argo-helm
helm install my-argo-cd argo/argo-cd --version 7.6.8 -n argocd
```
