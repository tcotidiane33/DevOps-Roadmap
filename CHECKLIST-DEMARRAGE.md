# ✅ CHECKLIST DÉMARRAGE DEVOPS

## 📋 Avant de Commencer

### Environnement de Développement
- [ ] **VS Code** installé
- [ ] Extensions VS Code :
  - [ ] GitLens
  - [ ] Docker
  - [ ] Kubernetes
  - [ ] Terraform
  - [ ] YAML
- [ ] **Terminal** configuré (iTerm2/Hyper recommandé)

### Comptes Créés
- [ ] **GitHub** account (gratuit)
- [ ] **Docker Hub** account
- [ ] **AWS** Free Tier OU **Azure** Free Account
- [ ] **Terraform Cloud** (optionnel, gratuit)

### Outils Installés

#### Essentiels (Semaine 1)
- [ ] **Git** (`brew install git`)
- [ ] **Docker Desktop** ([download](https://www.docker.com/products/docker-desktop))

#### Phase IAC (Semaine 3)
- [ ] **Terraform** (`brew install terraform`)
- [ ] **Ansible** (`brew install ansible`)
- [ ] **AWS CLI** (`brew install awscli`)

#### Phase Orchestration (Semaine 10+)
- [ ] **kubectl** (`brew install kubectl`)
- [ ] **Helm** (`brew install helm`)
- [ ] **minikube** OU **kind** pour k8s local

### Configuration Initiale

#### Git
```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre@email.com"
git config --global init.defaultBranch main
```

#### AWS CLI
```bash
aws configure
# AWS Access Key ID: [votre key]
# AWS Secret Access Key: [votre secret]
# Default region: eu-west-1
# Default output format: json
```

---

## 🗺️ Plan d'Apprentissage

### ✅ Prêt à Démarrer ?

**Phase 1 (Semaine 1-2) :** [GIT →](./GIT/README.md)  
**Phase 2 (Semaine 3-5) :** [DOCKER →](./CONTAINER/DOCKER/README.md)  
**Phase 3 (Semaine 6-11) :** [IAC (Terraform + Ansible) →](./IAC/PARCOURS-PEDAGOGIQUE.md)  

---

## 📊 Suivi de Progression

Créez votre journal d'apprentissage :
```bash
touch MON_PARCOURS.md
```

**Template quotidien :**
```markdown
## 2025-12-XX

### Ce que j'ai appris
- 

### Exercices complétés
- 

### Difficultés rencontrées
- 

### À faire demain
- 
```

---

## 🎯 Objectif Final (20 semaines)

**Vous serez capable de :**
- ✅ Gérer du code avec Git (workflows professionnels)
- ✅ Containeriser des applications (Docker)
- ✅ Provisionner des infrastructures (Terraform)
- ✅ Configurer des serveurs (Ansible)
- ✅ Déployer sur le cloud (AWS/Azure)
- ✅ Orchestrer avec Kubernetes
- ✅ Automatiser avec CI/CD
- ✅ Monitorer en production (Prometheus/Grafana)

**= DevOps Engineer Complet** 🚀

---

**Commencer maintenant :** [ROADMAP-DEVOPS.md](./ROADMAP-DEVOPS.md)
