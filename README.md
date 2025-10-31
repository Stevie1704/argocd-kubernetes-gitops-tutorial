# Argocd Kubernetes Gitops Tutorial

This repo contains all the code needed to follow along with our **[YouTube Tutorial](https://youtu.be/yj4O0wwkMQI)**.

## Prerequisites

To follow along with this tutorial, you'll need:
- Docker to start devcontainer, vscode
- A remote git repository (like GitHub)

## Install ArgoCD on your Cluster
```
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update
kubectl create namespace argocd
helm install argocd argo/argo-cd --namespace argocd
```

## Access ArgoCD UI

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Retrieve Credentials

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## API Calls

Here are commands that you can use to add grades to the Grade Submission API. **Windows Users should use Git Bash**.

```bash
curl -X POST http://localhost:<port>/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Harry", "subject": "Defense Against Dark Arts", "score": 95}'

curl -X POST http://localhost:<port>/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Ron", "subject": "Charms", "score": 82}'

curl -X POST http://localhost:<port>/grades \
  -H "Content-Type: application/json" \
  -d '{"name": "Hermione", "subject": "Potions", "score": 98}'
```

To verify, you can get all grades with:
```bash
curl http://localhost:<port>/grades
```

## Become a Cloud and DevOps Engineer

Learn every tool that matters: https://rayanslim.com
