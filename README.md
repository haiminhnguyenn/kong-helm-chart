# Kong Gateway & PostgreSQL Helm Chart Deployment via Argo CD

This repository contains Helm charts for deploying Kong Gateway in database mode (using PostgreSQL) on a Kubernetes cluster with Argo CD. It includes both the Admin API and Kong Manager GUI, allowing for a complete setup of Kong Gateway with a database-backed deployment.

## Prerequisites

Before deploying Kong Gateway and PostgreSQL via Argo CD, make sure you have the following:

- A Kubernetes cluster (Minikube, GKE, EKS, or any other Kubernetes setup)
- Helm CLI installed
- Argo CD installed and configured
- Access to Argo CD UI
- PostgreSQL and Kong Gateway Helm charts available in your repository
- GitHub repository linked with Argo CD

## Deployment Steps

> **Note:** This repository works with Argo CD installed in the `argocd` namespace of the Kubernetes cluster, and the `kong` namespace created in the Kubernetes cluster for deploying Kong Gateway and its database (PostgreSQL).

Applying manifest file directly to deploy the applications by pointing Argo CD to this repository.

1. Deploy PostgesSQL in `kong` namespace for Kong Gateway's database
```sh
kubectl apply -f postgresql-app.yaml
```

2. Deploy Kong Gateway in `kong` namespace
```sh
kubectl apply -f kong-gateway-app.yaml
```

## Access Kong Manager and Admin API
- Admin API:  `http://<external-ip>:8001`
- Kong Manager GUI:  `http://<external-ip>:8002`

These URLs can be exposed using LoadBalancer service depending on your Kubernetes configuration.
