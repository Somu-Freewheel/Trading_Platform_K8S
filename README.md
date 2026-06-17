# Trading Platform K8S

A Kubernetes-deployed trading application with PostgreSQL database backend.

## Project Overview

This project sets up a complete trading platform infrastructure using Kubernetes, including:
- PostgreSQL database deployment
- Trading application microservice
- Namespace isolation for the trading app

## Prerequisites

- Docker
- Kubernetes cluster (Minikube, Docker Desktop K8S, or cloud provider)
- kubectl CLI
- IntelliJ IDEA 2024.3.5 (for development)

## Setup Instructions

### 1. Create Namespace

```bash
kubectl apply -f namespaces/trading-app.yaml
````

2. Deploy PostgreSQL
   kubectl apply -f postgres/deployment.yaml
   kubectl apply -f postgres/service.yaml

3. Deploy Trading Application
   kubectl apply -f trading-app/deployment.yaml
   kubectl apply -f trading-app/service.yaml

# Important Commands
# Check cluster status
kubectl get nodes

# List all resources in trading-app namespace
kubectl get all -n trading-app

# View deployments
kubectl get deployments -n trading-app

# View pods
kubectl get pods -n trading-app

# View services
kubectl get svc -n trading-app

# View PostgreSQL logs
kubectl logs -n trading-app deployment/postgres

# View trading-app logs
kubectl logs -n trading-app deployment/trading-app

# Describe deployment
kubectl describe deployment postgres -n trading-app

# Port forward to PostgreSQL
kubectl port-forward -n trading-app svc/postgres 5432:5432

# Port forward to trading-app
kubectl port-forward -n trading-app svc/trading-app 8080:8080

# Connect to PostgreSQL pod
kubectl exec -it -n trading-app <pod-name> -- psql -U postgres -d trading_db

# Database credentials
# Username: postgres
# Password: user123
# Database: trading_db
# Port: 5432




