# https://github.com/KONDRONETWORKS/DevOps-Roadmap.git
# 📚 STRUCTURE DEVOPS - Vue d'Ensemble

## 🗂️  Organisation du Repository

```
DEVOPS/
├── 📘 ROADMAP-DEVOPS.md          ← 🎯 COMMENCER ICI
├── 📋 CHECKLIST-DEMARRAGE.md     ← Setup initial
│
├── GIT/                          Phase 1 (2 sem)
│   ├── README.md                 Guide complet Git
│   ├── CI/README.md              CI/CD Pipelines
│   └── exercices/                Exercices pratiques
│
├── CONTAINER/                    Phase 2 (3 sem)
│   ├── DOCKER/
│   │   ├── README.md             Guide Docker complet
│   │   └── exercices/
│   ├── PODMAN/
│   └── LXC/
│
├── IAC/                          Phase 3 (6 sem) ✅
│   ├── README.md                 Vue d'ensemble
│   ├── PARCOURS-PEDAGOGIQUE.md   Méthodologie
│   ├── CONCEPTS-PEDAGOGIQUES.md  Concepts
│   ├── semaine-1-2-terraform-basics/
│   ├── semaine-3-4-terraform-avance/
│   ├── semaine-5-ansible/
│   └── semaine-6-integration/
│
├── CLOUD/                        Phase 4 (3 sem)
│   ├── AWS/
│   │   ├── README.md             Services essentiels
│   │   └── exercices/
│   ├── AZURE/
│   └── GCP/
│
├── ORCHESTRATION/                Phase 5 (4 sem)
│   └── K8S/
│       ├── README.md             Guide Kubernetes
│       └── exercices/
│
└── MONITORING/                   Phase 7 (2 sem)
    ├── PROMETHEUS/
    │   ├── README.md             Métriques
    │   └── exercices/
    ├── GRAFANA/
    │   ├── README.md             Dashboards
    │   └── exercices/
    └── ELECTICSTACK/

```

---

## 🎯 Parcours Recommandé

### Pour Débutants Complets
```
1. Lire ROADMAP-DEVOPS.md
2. Suivre CHECKLIST-DEMARRAGE.md (setup)
3. Phase 1: GIT/ (2 semaines)
4. Phase 2: CONTAINER/DOCKER/ (3 semaines)
5. Phase 3: IAC/ (6 semaines)
6. Phase 4: CLOUD/AWS/ (3 semaines)
7. Phase 5: ORCHESTRATION/K8S/ (4 semaines)
8. Phase 6: GIT/CI/ (2 semaines)
9. Phase 7: MONITORING/ (2 semaines)
```

**Durée totale :** 20-24 semaines (5-6 mois)

### Pour Personnes avec Bases
- **Connais Git ?** → Sauter Phase 1
- **Connais Docker ?** → Commencer Phase 3 (IAC)
- **Connais Terraform ?** → Commencer Phase 4 (Cloud) ou 5 (K8s)

---

## 📖 Documents par Objectif

### Je veux comprendre la big picture
→ [`ROADMAP-DEVOPS.md`](./ROADMAP-DEVOPS.md)

### Je veux setup mon environnement
→ [`CHECKLIST-DEMARRAGE.md`](./CHECKLIST-DEMARRAGE.md)

### Je veux apprendre Git
→ [`GIT/README.md`](./GIT/README.md)

### Je veux apprendre Docker
→ [`CONTAINER/DOCKER/README.md`](./CONTAINER/DOCKER/README.md)

### Je veux apprendre Terraform/Ansible (IAC)
→ [`IAC/PARCOURS-PEDAGOGIQUE.md`](./IAC/PARCOURS-PEDAGOGIQUE.md)

### Je veux apprendre Kubernetes
→ [`ORCHESTRATION/K8S/README.md`](./ORCHESTRATION/K8S/README.md)

### Je veux apprendre CI/CD
→ [`GIT/CI/README.md`](./GIT/CI/README.md)

### Je veux apprendre le Monitoring
→ [`MONITORING/PROMETHEUS/README.md`](./MONITORING/PROMETHEUS/README.md)

---

## 📊 Statut des Modules

| Module | Statut | Documentation | Exercices |
|--------|--------|---------------|-----------|
| **GIT** | ✅ Complet | README.md créé | À créer |
| **DOCKER** | ✅ Complet | README.md créé | À créer |
| **IAC** | ✅ Complet | Documentation riche | Exercices présents |
| **AWS** | ✅ Essentiel | README.md créé | À créer |
| **KUBERNETES** | ✅ Complet | README.md créé | À créer |
| **CI/CD** | ✅ Complet | README.md créé | À créer |
| **PROMETHEUS** | ✅ Essentiel | README.md créé | À créer |
| **GRAFANA** | ✅ Essentiel | README.md créé | À créer |
| **AZURE** | 🟡 À créer | - | - |
| **GCP** | 🟡 À créer | - | - |
| **PODMAN** | 🟡 À créer | - | - |

---

## 🎓 Progression Typique

**Mois 1-2 :** Fondations (Git + Docker)  
**Mois 3-4 :** Infrastructure (Terraform + Ansible)  
**Mois 5 :** Cloud (AWS)  
**Mois 6 :** Orchestration (Kubernetes + CI/CD + Monitoring)

---

## 💡 Conseils d'Utilisation

### Navigation Optimale
1. **Top-down** : Lire la roadmap globale d'abord
2. **Focus** : Se concentrer sur UN module à la fois
3. **Pratique** : Faire TOUS les exercices
4. **Documentation** : Tenir un journal d'apprentissage

### Utilisation des README
- **Semaine-type** : Section "Parcours d'apprentissage"
- **Référence rapide** : Section "Commandes essentielles"
- **Approfondissement** : Section "Concepts pédagogiques"

---

**🚀 Prêt à commencer ?** → [`ROADMAP-DEVOPS.md`](./ROADMAP-DEVOPS.md)

*"The expert in anything was once a beginner"*
