# 📋 Guide des Exercices - Tous Modules

## 🎯 Structure des Exercices

Chaque exercice suit le format :
- 🎯 **Objectifs** : Ce que vous allez apprendre
- ⏱️ **Durée** : Temps estimé
- 📋 **Prérequis** : Ce qu'il faut savoir avant
- 📚 **Parties** : Étapes détaillées
- ✅ **Validation** : Comment vérifier
- ➡️ **Prochaine étape** : Exercice suivant

---

## 🟢 GIT - 10 Exercices (3 semaines)

### Semaine 1 : Fondamentaux

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 01 | [Installation](./GIT/exercices/01-installation) | Installer et configurer Git | 30min | ✅ Créé |
| 02 | Premier Repository | init, add, commit, log | 1h | 🔨 Créer |
| 03 | Remote GitHub | clone, push, pull, remote | 1h30 | 🔨 Créer |

### Semaine 2 : Collaboration

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 04 | Branches | branch, checkout, merge | 2h | 🔨 Créer |
| 05 | Merge & Conflits | Résoudre conflits | 3h | 🔨 Créer |
| 06 | Pull Requests | Workflow collaboratif | 2h | 🔨 Créer |
| 07 | Git Flow | Feature, release, hotfix | 3h | 🔨 Créer |

### Semaine 3 : Avancé

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 08 | Rebase | Rebase vs merge, --interactive | 2h | 🔨 Créer |
| 09 | Commandes Avancées | stash, cherry-pick, reset | 2h | 🔨 Créer |
| 10 | Git Hooks | Automatisation pre-commit/push | 2h | 🔨 Créer |

**Total : ~19 heures**

---

## 🐳 DOCKER - 10 Exercices (3 semaines)

### Semaine 1 : Basics

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 01 | Installation | Installer Docker Desktop | 30min | 🔨 Créer |
| 02 | Premiers Containers | docker run, stop, rm, ps | 1h | 🔨 Créer |
| 03 | Docker CLI | Images, containers, logs | 1h30 | 🔨 Créer |
| 04 | [Dockerfile](./CONTAINER/DOCKER/exercices/04-dockerfile) | Créer images FROM, COPY, RUN | 2h | ✅ Créé |
| 05 | App Node.js | Containeriser app complète | 2h | 🔨 Créer |

### Semaine 2 : Intermédiaire

| # | Exercice |Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 06 | Volumes | Persistence avec volumes | 1h30 | 🔨 Créer |
| 07 | Networks | Communication inter-containers | 1h30 | 🔨 Créer |
| 08 | Docker Compose | Stack multi-services | 2h | 🔨 Créer |

### Semaine 3 : Avancé

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 09 | Multi-Stage Build | Optimisation taille images | 2h | 🔨 Créer |
| 10 | Projet Final | App full-stack (frontend+backend+db) | 4h | 🔨 Créer |

**Total : ~18 heures**

---

## ☸️ KUBERNETES - 18 Exercices (4 semaines)

### Semaine 1 : Fondamentaux

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 01 | Installation minikube | Setup cluster local | 1h | 🔨 Créer |
| 02 | Premier Pod | Créer et gérer pods | 1h | 🔨 Créer |
| 03 | kubectl Basics | Commands essentielles | 1h30 | 🔨 Créer |
| 04 | Deployments | Replicas, rolling updates | 2h | 🔨 Créer |
| 05 | Services | ClusterIP, NodePort, LoadBalancer | 2h | 🔨 Créer |
| 06 | ConfigMaps | Configuration externalisée | 1h30 | 🔨 Créer |
| 07 | Secrets | Gestion secrets | 1h30 | 🔨 Créer |

### Semaine 2 : Stockage & Networking

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 08 | Volumes | Volumes types | 2h | 🔨 Créer |
| 09 | PV et PVC | Persistent storage | 2h | 🔨 Créer |
| 10 | StatefulSet | Apps stateful (DB) | 3h | 🔨 Créer |
| 11 | Ingress | HTTP routing | 2h | 🔨 Créer |
| 12 | Network Policies | Firewall pods | 2h | 🔨 Créer |

### Semaine 3 : Sécurité & Performance

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 13 | RBAC | Roles, RoleBindings | 3h | 🔨 Créer |
| 14 | Resources & Limits | CPU/Memory management | 2h | 🔨 Créer |
| 15 | HPA | Horizontal Pod Autoscaler | 3h | 🔨 Créer |

### Semaine 4 : Production

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 16 | Helm | Package manager | 3h | 🔨 Créer |
| 17 | ArgoCD | GitOps deployment | 4h | 🔨 Créer |
| 18 | Projet Final | App microservices complète | 6h | 🔨 Créer |

**Total : ~40 heures**

---

## ☁️ CLOUD/AWS - 12 Exercices (3 semaines)

### Semaine 1 : Services de Base

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 01 | Compte & IAM | Setup compte, users, roles | 1h | 🔨 Créer |
| 02 | EC2 Basics | Lancer VMs | 2h | 🔨 Créer |
| 03 | S3 Storage | Object storage, buckets | 1h30 | 🔨 Créer |
| 04 | VPC Networking | Réseaux privés, subnets | 2h | 🔨 Créer |

### Semaine 2 : Services Avancés

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 05 | RDS Database | Bases managées | 2h | 🔨 Créer |
| 06 | Load Balancer | ELB, ALB | 2h | 🔨 Créer |
| 07 | Auto Scaling | Scaling automatique | 2h | 🔨 Créer |
| 08 | CloudFormation | IaC AWS-natif | 3h | 🔨 Créer |

### Semaine 3 : DevOps

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 09 | CodePipeline | CI/CD AWS | 3h | 🔨 Créer |
| 10 | CloudWatch | Monitoring & logs | 2h | 🔨 Créer |
| 11 | Lambda | Serverless functions | 2h | 🔨 Créer |
| 12 | Projet Final | App 3-tiers complète | 5h | 🔨 Créer |

**Total : ~27 heures**

---

## 📊 MONITORING - 8 Exercices (2 semaines)

### Semaine 1 : Prometheus & Métriques

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 01 | Install Prometheus | Setup stack | 1h | 🔨 Créer |
| 02 | Métriques Basics | Scraping, targets | 1h30 | 🔨 Créer |
| 03 | PromQL | Queries, aggregation | 2h | 🔨 Créer |
| 04 | Alertmanager | Alertes & notifications | 2h | 🔨 Créer |

### Semaine 2 : Grafana & Dashboards

| # | Exercice | Objectifs | Durée | Status |
|---|----------|-----------|-------|--------|
| 05 | Grafana Setup | Install & datasources | 1h | 🔨 Créer |
| 06 | Premier Dashboard | Panels, variables | 2h | 🔨 Créer |
| 07 | K8s Monitoring | Monitor cluster K8s | 3h | 🔨 Créer |
| 08 | Projet Final | Stack monitoring complète | 4h | 🔨 Créer |

**Total : ~16 heures**

---

## 📊 Récapitulatif Global

| Module | Exercices | Durée Totale | Semaines |
|--------|-----------|--------------|----------|
| **GIT** | 10 | ~19h | 3 |
| **DOCKER** | 10 | ~18h | 3 |
| **KUBERNETES** | 18 | ~40h | 4 |
| **AWS** | 12 | ~27h | 3 |
| **MONITORING** | 8 | ~16h | 2 |
| **IAC** | 19 | ~60h | 6 ✅ |
| **TOTAL** | **77** | **~180h** | **21 semaines** |

---

## 🎯 Comment Utiliser Ce Guide

### Pour Chaque Exercice

1. **Lire README** du module associé
2. **Comprendre concepts** (CONCEPTS-PEDAGOGIQUES.md)
3. **Faire exercice** étape par étape
4. **Valider** avec checkpoints
5. **Documenter** dans journal d'apprentissage

### Template Journal

```markdown
## Exercice XX : [Nom]
**Date :** 2025-12-XX
**Durée réelle :** Xh
**Difficulté :** ⭐⭐⭐

### Ce que j'ai appris
-

### Difficultés rencontrées
-

### Solutions trouvées
-

### À revoir
-
```

---

## 🔨 Statut de Création

### ✅ Créés (Exemples)
- GIT/exercices/01-installation
- DOCKER/exercices/04-dockerfile
- IAC/* (tous les exercices ✅)

### 🔨 À Créer
Tous les autres exercices suivent la même structure :
- 🎯 Objectifs
- ⏱️ Durée
- 📚 Parties avec code
- ✅ Validation
- ➡️ Prochaine étape

---

## 📝 Note pour Créer un Exercice

Utiliser le template :

```markdown
# Exercice XX : [Titre]

## 🎯 Objectifs
## ⏱️ Durée Estimée
## 📋 Prérequis
## 📚 Partie 1 : [Nom]
### Code/Commandes
### Explication
## ✅ Validation
## ➡️ Prochaine Étape
## 📚 Ressources
```

---

**Voir aussi :**
- [Retour Roadmap](./ROADMAP-DEVOPS.md)
- [Structure Modules](./STATUT-MODULES.md)
