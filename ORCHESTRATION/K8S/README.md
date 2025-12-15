# ☸️ KUBERNETES (K8S) - Orchestration de Containers

## 🎯 Pourquoi Kubernetes ?

Docker gère les containers, Kubernetes les **orchestre** à grande échelle :
- ✅ **Auto-scaling** : Adaptation automatique à la charge
- ✅ **Self-healing** : Redémarrage auto des containers crashés
- ✅ **Load Balancing** : Distribution du trafic
- ✅ **Rolling Updates** : Déploiements sans downtime
- ✅ **Service Discovery** : Communication inter-services
- ✅ **Secrets Management** : Gestion sécurisée des credentials

**En bref :** Docker = Containers | Kubernetes = Production-Grade Container Orchestration

---

## 📚 Parcours d'Apprentissage (4 semaines)

### Semaine 1 : Concepts Fondamentaux

#### Jour 1-2 : Architecture K8s
**Composants :**
- **Control Plane** : API Server, Scheduler, Controller Manager, et etcd
- **Worker Nodes** : Kubelet, Kube-proxy, Container Runtime
- **Pods** : Plus petite unité déployable (1+ containers)

**Exercices :**
- [01: Installation (minikube/kind)](./exercices/01-installation)
- [02: Premier Pod](./exercices/02-premier-pod)
- [03: kubectl Basics](./exercices/03-kubectl)

#### Jour 3-5 : Workloads de Base
**Ressources essentielles :**
- **Pods** : Container(s) packagés ensemble
- **Deployments** : Gestion de réplicas + rolling updates
- **ReplicaSets** : Maintien du nombre de pods
- **Services** : Exposition réseau des pods

**Exercices :**
- [04: Deployments](./exercices/04-deployments)
- [05: Services](./exercices/05-services)
- [06: App Multi-tiers](./exercices/06-app-multitiers)

#### Jour 6-7 : Configuration
**ConfigMaps & Secrets :**
- ConfigMaps : Configuration non-sensible
- Secrets : Données sensibles (passwords, tokens)
- Environment variables
- Volume mounts

**Exercices :**
- [07: ConfigMaps](./exercices/07-configmaps)
- [08: Secrets](./exercices/08-secrets)
- [09: App avec Config](./exercices/09-app-config)

### Semaine 2 : Stockage et Networking

#### Jour 8-10 : Stockage Persistant
**Volumes :**
- emptyDir, hostPath
- **PersistentVolumes (PV)**
- **PersistentVolumeClaims (PVC)**
- **StorageClasses**
- **StatefulSets** (pour apps stateful)

**Exercices :**
- [10: Volumes](./exercices/10-volumes)
- [11: PV et PVC](./exercices/11-pv-pvc)
- [12: StatefulSet (DB)](./exercices/12-statefulset)

#### Jour 11-14 : Networking Avancé
**Concepts :**
- ClusterIP, NodePort, LoadBalancer
- **Ingress** (reverse proxy L7)
- **Network Policies** (firewall pods)
- DNS interne

**Exercices :**
- [13: Services Types](./exercices/13-service-types)
- [14: Ingress](./exercices/14-ingress)
- [15: Network Policies](./exercices/15-network-policies)

### Semaine 3 : Concepts Avancés

#### Jour 15-17 : Sécurité
**RBAC & Sécurité :**
- **ServiceAccounts**
- **Roles & RoleBindings**
- **ClusterRoles & ClusterRoleBindings**
- Pod Security Standards
- Security Contexts

**Exercices :**
- [16: ServiceAccounts](./exercices/16-serviceaccounts)
- [17: RBAC](./exercices/17-rbac)
- [18: Pod Security](./exercices/18-pod-security)

#### Jour 18-21 : Scaling et Performance
**Auto-scaling :**
- **HPA** (Horizontal Pod Autoscaler)
- **VPA** (Vertical Pod Autoscaler)
- **Cluster Autoscaler**
- Resource Requests & Limits
- QoS Classes

**Exercices :**
- [19: Resources](./exercices/19-resources)
- [20: HPA](./exercices/20-hpa)
- [21: Stress Test](./exercices/21-stress-test)

### Semaine 4 : Production & GitOps

#### Jour 22-24 : Helm (Package Manager)
**Helm Charts :**
- Templates
- Values
- Dependencies
- Chart Repository

**Exercices :**
- [22: Helm Basics](./exercices/22-helm-basics)
- [23: Custom Chart](./exercices/23-custom-chart)
- [24: Multi-env avec Helm](./exercices/24-helm-multienv)

#### Jour 25-28 : GitOps & CI/CD
**GitOps avec ArgoCD/FluxCD :**
- Git as Source of Truth
- Automated Sync
- Rollback capabilities

**Exercices :**
- [25: ArgoCD Setup](./exercices/25-argocd)
- [26: GitOps Workflow](./exercices/26-gitops)
- [27: CI/CD Pipeline](./exercices/27-cicd-pipeline)
- [Projet Final: App Production](./projet-final)

---

## 🛠️ Commandes kubectl Essentielles

### Cluster Info
```bash
# Version kubectl
kubectl version

# Infos cluster
kubectl cluster-info

# Nodes du cluster
kubectl get nodes

# Contextes (multi-clusters)
kubectl config get-contexts
kubectl config use-context minikube
```

### Pods
```bash
# Lister les pods
kubectl get pods
kubectl get pods -n namespace-name
kubectl get pods -A  # Tous les namespaces

# Détails d'un pod
kubectl describe pod mon-pod

# Logs
kubectl logs mon-pod
kubectl logs -f mon-pod  # Follow
kubectl logs mon-pod -c container-name  # Multi-container

# Exécuter une commande
kubectl exec -it mon-pod -- sh
kubectl exec mon-pod -- env

# Port-forward (accès local)
kubectl port-forward mon-pod 8080:80
```

### Deployments
```bash
# Créer un deployment
kubectl create deployment nginx --image=nginx:latest

# Lister deployments
kubectl get deployments

# Scaler
kubectl scale deployment nginx --replicas=5

# Rolling update
kubectl set image deployment/nginx nginx=nginx:1.21

# Rollback
kubectl rollout undo deployment/nginx

# Historique
kubectl rollout history deployment/nginx

# Status du rollout
kubectl rollout status deployment/nginx
```

### Services
```bash
# Créer un service
kubectl expose deployment nginx --port=80 --type=LoadBalancer

# Lister services
kubectl get svc

# Details
kubectl describe svc nginx
```

### Configuration
```bash
# ConfigMap
kubectl create configmap app-config --from-literal=env=prod

# Secret
kubectl create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password=secret123

# Voir le contenu (base64 encoded)
kubectl get secret db-secret -o yaml

# Decoder
kubectl get secret db-secret -o jsonpath='{.data.password}' | base64 -d
```

### Debugging
```bash
# Events du cluster
kubectl get events --sort-by=.metadata.creationTimestamp

# Top (ressources)
kubectl top nodes
kubectl top pods

# Décrire (debugging)
kubectl describe pod mon-pod

# Logs de tous les pods d'un deployment
kubectl logs -l app=nginx --tail=50
```

### Apply (Declarative)
```bash
# Appliquer un manifest
kubectl apply -f deployment.yaml

# Appliquer un dossier
kubectl apply -f ./k8s-manifests/

# Dry-run (test sans appliquer)
kubectl apply -f deployment.yaml --dry-run=client

# Diff (changements)
kubectl diff -f deployment.yaml

# Delete
kubectl delete -f deployment.yaml
kubectl delete deployment nginx
```

---

## 📖 Manifests YAML - Exemples

### Deployment Complet
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: webapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: app
        image: monapp:1.0
        ports:
        - containerPort: 8080
        
        # Resources (requests = minimum, limits = maximum)
        resources:
          requests:
            memory: "128Mi"
            cpu: "250m"
          limits:
            memory: "256Mi"
            cpu: "500m"
        
        # Variables d'environnement
        env:
        - name: ENV
          value: "production"
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: password
        
        # ConfigMap as env vars
        envFrom:
        - configMapRef:
            name: app-config
        
        # Health checks
        livenessProbe:
          httpGet:
            path: /health
            port: 8080
          initialDelaySeconds: 30
          periodSeconds: 10
        
        readinessProbe:
          httpGet:
            path: /ready
            port: 8080
          initialDelaySeconds: 5
          periodSeconds: 5
        
        # Volumes
        volumeMounts:
        - name: data
          mountPath: /app/data
        - name: config
          mountPath: /app/config
      
      volumes:
      - name: data
        persistentVolumeClaim:
          claimName: app-pvc
      - name: config
        configMap:
          name: app-config
```

### Service (LoadBalancer)
```yaml
apiVersion: v1
kind: Service
metadata:
  name: webapp-service
spec:
  type: LoadBalancer
  selector:
    app: webapp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
```

### Ingress (Reverse Proxy)
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: webapp-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx
  rules:
  - host: monapp.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: webapp-service
            port:
              number: 80
  tls:
  - hosts:
    - monapp.example.com
    secretName: tls-secret
```

### HPA (Horizontal Pod Autoscaler)
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: webapp-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: webapp
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
```

---

## 🎯 Architecture d'une App sur K8s

```
Internet
    ↓
Ingress (HTTPS + Routing)
    ↓
┌─────────────────────────────────┐
│         Services                │
├─────────────────────────────────┤
│  Frontend   API    Database     │
│  Service    Svc    Svc (HL)     │
└─────────────────────────────────┘
    ↓           ↓          ↓
┌──────────┐ ┌──────┐ ┌──────────┐
│ Frontend │ │ API  │ │ Database │
│ Pods (3) │ │ Pods │ │StatefulSet
└──────────┘ └──────┘ └──────────┘
                ↓
        ConfigMaps & Secrets
                ↓
        PersistentVolumes
```

---

## 🔒 Best Practices Sécurité

### 1. RBAC (Role-Based Access Control)
```yaml
# Role (namespace-scoped)
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: pod-reader
  namespace: default
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list"]

---
# RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: ServiceAccount
  name: my-sa
  namespace: default
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

### 2. Network Policies
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-all-ingress
spec:
  podSelector: {}
  policyTypes:
  - Ingress
  # Pas de 'ingress:' = Deny all
```

### 3. Security Context
```yaml
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  fsGroup: 2000
  capabilities:
    drop:
    - ALL
  readOnlyRootFilesystem: true
```

---

## 📊 Exercices Pratiques

| # | Exercice | Compétences | Durée |
|---|----------|-------------|-------|
| 01 | Installation | minikube/kind | 1h |
| 02-03 | Pods & kubectl | Basics | 1h30 |
| 04-06 | Deployments & Services | Core workloads | 3h |
| 07-09 | Config & Secrets | Configuration | 2h |
| 10-12 | Volumes & StatefulSets | Stockage | 4h |
| 13-15 | Networking | Services & Ingress | 3h |
| 16-18 | Sécurité RBAC | RBAC | 3h |
| 19-21 | Scaling | HPA/VPA | 3h |
| 22-24 | Helm | Packaging | 4h |
| 25-27 | GitOps | CI/CD | 4h |

---

## ✅ Certifications

### CKA (Certified Kubernetes Administrator)
- **Niveau :** Avancé
- **Coût :** $395
- **Durée exam :** 2h (hands-on)
- **Validité :** 3 ans
- [Plus d'infos](https://www.cncf.io/certification/cka/)

### CKAD (Certified Kubernetes Application Developer)
- **Niveau :** Intermédiaire
- **Coût :** $395
- **Focus :** Développement d'apps sur K8s

### CKS (Certified Kubernetes Security Specialist)
- **Niveau :** Expert
- **Pré-requis :** CKA
- **Focus :** Sécurité

---

## 🚀 Outils Complémentaires

| Outil | Usage |
|-------|-------|
| **Helm** | Package manager |
| **ArgoCD** | GitOps CD |
| **Lens** | IDE visuel K8s |
| **k9s** | Terminal UI |
| **Kustomize** | Configuration management |
| **Istio** | Service mesh |
| **Prometheus** | Monitoring |
| **Grafana** | Dashboards |

---

**Prochaine étape :** [CI/CD](../../GIT/CI/README.md) 🚀

*"Kubernetes: Making distributed systems boring since 2014"*
