# Final Project: E-Commerce Application

This directory contains a complete Kubernetes deployment for an e-commerce application demonstrating all concepts learned.

## Architecture

```
Internet
   ↓
Ingress (mon-app.local)
   ↓
Frontend Service (ClusterIP)
   ↓
Frontend Deployment (3 replicas, HPA enabled)
   ↓
Backend Service (ClusterIP)
   ↓
Backend Deployment (3 replicas, with Resources)
   ↓  (Network Policy)
Database StatefulSet (Postgres, PVC)
   ↓
Redis Deployment (Cache)
```

## Components

### 1. Frontend
- **Deployment**: 3 replicas with resource limits
- **HPA**: Auto-scales between 2-10 based on CPU
- **ConfigMap**: Configuration variables
- **Service**: ClusterIP

### 2. Backend
- **Deployment**: 3 replicas with  health checks
- **Secret**: Database credentials
- **Service**: ClusterIP
- **Resources**: CPU/Memory limits

### 3. Database
- **StatefulSet**: Persistent storage
- **PVC**: 10Gi storage per replica
- **Network Policy**: Only backend can access
- **Service**: Headless service

### 4. Redis
- **Deployment**: Single replica
- **Service**: ClusterIP

### 5. Ingress
- Routes traffic to frontend

## Deployment Order

```bash
# 1. ConfigMaps and Secrets
kubectl apply -f configmaps/
kubectl apply -f secrets/

# 2. Database (StatefulSet)
kubectl apply -f database/

# 3. Redis
kubectl apply -f redis/

# 4. Backend
kubectl apply -f backend/

# 5. Frontend
kubectl apply -f frontend/

# 6. Ingress
kubectl apply -f ingress/

# 7. Network Policy
kubectl apply -f network-policies/

# 8. HPA
kubectl apply -f hpa/
```

## Verification

```bash
# Check all resources
kubectl get all

# Check persistent volumes
kubectl get pvc

# Check network policies
kubectl get networkpolicies

# Check HPA
kubectl get hpa

# Access application
# Add to /etc/hosts: <minikube-ip> mon-app.local
# Visit: http://mon-app.local
```

## RBAC

ServiceAccount `app-deployer` is configured with permissions to:
- Read pods, services, deployments
- Edit configmaps
- No permission to delete resources

## Helm Chart

A Helm chart is provided in `helm/` directory to deploy the entire stack with:
```bash
helm install ecommerce ./helm/ecommerce-chart
```

## GitOps (ArgoCD)

ArgoCD application manifest is in `argocd/app.yaml` for automated deployment.

## Congratulations! 🎓

You have mastered Kubernetes!
