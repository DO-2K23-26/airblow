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

## Installation de Postgres-ha

```bash
kubectl create namespace airflow
kubectl apply -f ./infrastructure/application.yaml -n argocd
```

## Installation de airflow

You will an ssh key to access the dags that are github.

```bash
ssh-keygen
```

Then create the secret for airflow to access your github repo:

```bash
kubectl create secret generic airflow-ssh-key --from-file=gitSshKey=airflow_key -n airflow
```

Add the key to the GitHub repo:
    - Settings → Deploy keys → Add Deploy Key.
    - Check "Allow write access" .


```bash
kubectl create namespace airflow
kubectl apply -f ./airflow/application.yaml -n argocd
```