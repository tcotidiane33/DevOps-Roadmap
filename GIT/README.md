# 🌿 GIT - Versioning de Code

## 🎯 Pourquoi Git est Essentiel en DevOps

Git est **LA** fondation de tout workflow DevOps :
- ✅ Versioning du code d'infrastructure (IaC)
- ✅ Collaboration en équipe
- ✅ Traçabilité des changements
- ✅ Base du CI/CD
- ✅ Documentation automatique

---

## 📚 Parcours d'Apprentissage (2 semaines)

### Semaine 1 : Fondamentaux

#### Jour 1-2 : Concepts de Base
**Concepts clés :**
- Repository (local vs remote)
- Commit (snapshot)
- Branch (ligne de développement)
- Merge (fusion de branches)

**Exercices :**
- [Exercice 01: Installation et Configuration](./exercices/01-installation)
- [Exercice 02: Premier Repository](./exercices/02-premier-repo)
- [Exercice 03: Commits Atomiques](./exercices/03-commits)

#### Jour 3-4 : Branches et Merge
**Concepts clés :**
- Création de branches
- Switching entre branches
- Merge fast-forward vs 3-way
- Résolution de conflits

**Exercices :**
- [Exercice 04: Branches](./exercices/04-branches)
- [Exercice 05: Merge et Conflits](./exercices/05-merge-conflits)

#### Jour 5-7 : Remote et Collaboration
**Concepts clés :**
- Clone, Pull, Push
- Remote repositories (GitHub/GitLab)
- Fork et Pull Requests
- Code Review

**Exercices :**
- [Exercice 06: Remote Repositories](./exercices/06-remote)
- [Exercice 07: Pull Requests](./exercices/07-pull-requests)

### Semaine 2 : Avancé

#### Jour 8-10 : Git Workflows
**Workflows professionnels :**
- **Git Flow** : feature/develop/release/hotfix
- **GitHub Flow** : main + feature branches
- **Trunk-Based Development** : commits fréquents sur main

**Exercices :**
- [Exercice 08: Git Flow](./exercices/08-git-flow)
- [Exercice 09: GitHub Flow](./exercices/09-github-flow)

#### Jour 11-12 : Commandes Avancées
**Concepts clés :**
- Rebase (réécriture d'historique)
- Cherry-pick (sélection de commits)
- Stash (mise de côté temporaire)
- Reset vs Revert

**Exercices :**
- [Exercice 10: Rebase](./exercices/10-rebase)
- [Exercice 11: Commandes Avancées](./exercices/11-avancees)

#### Jour 13-14 : Automatisation
**Concepts clés :**
- Git Hooks (pre-commit, pre-push)
- Aliases Git
- Git Submodules
- Git LFS (Large File Storage)

**Exercices :**
- [Exercice 12: Git Hooks](./exercices/12-hooks)
- [Projet Final: Workflow Complet](./projet-final)

---

## 🛠️ Commandes Essentielles

### Configuration Initiale
```bash
# Configuration utilisateur
git config --global user.name "Votre Nom"
git config --global user.email "votre@email.com"

# Éditeur par défaut
git config --global core.editor "code --wait"

# Affichage couleurs
git config --global color.ui auto
```

### Workflow de Base
```bash
# Initialiser un repo
git init

# Cloner un repo distant
git clone https://github.com/user/repo.git

# Statut des fichiers
git status

# Ajouter des fichiers
git add fichier.txt        # Un fichier
git add .                  # Tous les fichiers

# Commit
git commit -m "Message descriptif"

# Push vers remote
git push origin main

# Pull depuis remote
git pull origin main
```

### Gestion des Branches
```bash
# Créer une branche
git branch feature/ma-feature

# Basculer sur une branche
git checkout feature/ma-feature

# Créer ET basculer (raccourci)
git checkout -b feature/nouvelle-feature

# Lister les branches
git branch                 # Locales
git branch -a              # Toutes (locales + remote)

# Merger une branche
git checkout main
git merge feature/ma-feature

# Supprimer une branche
git branch -d feature/ma-feature     # Locale
git push origin --delete feature/ma-feature  # Remote
```

### Résolution de Conflits
```bash
# En cas de conflit lors du merge
# 1. Voir les fichiers en conflit
git status

# 2. Éditer les fichiers (résoudre les <<<< ==== >>>>)

# 3. Marquer comme résolu
git add fichier-resolu.txt

# 4. Finaliser le merge
git commit
```

### Commandes Avancées
```bash
# Rebase (réécrire l'historique)
git rebase main

# Rebase interactif (modifier plusieurs commits)
git rebase -i HEAD~3

# Stash (mettre de côté)
git stash
git stash list
git stash pop

# Cherry-pick (appliquer un commit spécifique)
git cherry-pick abc1234

# Reset (annuler des commits)
git reset --soft HEAD~1    # Garde les changements
git reset --hard HEAD~1    # SUPPRIME les changements

# Revert (annuler en créant un nouveau commit)
git revert abc1234
```

---

## 📖 Concepts Pédagogiques

### 1. Qu'est-ce qu'un Commit ?
**Analogie :** Une photo (snapshot) de votre code à un instant T

```
Commit 1: Photo du projet le 01/12
Commit 2: Photo du projet le 02/12
Commit 3: Photo du projet le 03/12
```

### 2. Branches : Développement Parallèle
```
main        : A --- B --- C --- F --- G
                    \           /
feature/auth:        D --- E ---
```

### 3. Merge vs Rebase

**Merge** (fusion)
```
main    : A --- B --- C --- M
                \           /
feature :        D --- E ---
```

**Rebase** (réécriture)
```
main    : A --- B --- C --- D' --- E'
```

---

## 🎯 Best Practices

### Messages de Commit
❌ **Mauvais**
```
Update
Fix bug
Changes
```

✅ **Bons**
```
feat: Add user authentication
fix: Resolve login timeout issue
docs: Update README with setup instructions
refactor: Extract database logic into separate module
```

**Convention:** [Conventional Commits](https://www.conventionalcommits.org/)
- `feat:` Nouvelle fonctionnalité
- `fix:` Correction de bug
- `docs:` Documentation
- `refactor:` Refactoring
- `test:` Tests
- `chore:` Tâches diverses

### Structure de Branches
```
main/master       → Production
develop           → Intégration
feature/*         → Nouvelles fonctionnalités
bugfix/*          → Corrections de bugs
hotfix/*          → Corrections urgentes en prod
release/*         → Préparation de release
```

### .gitignore
```
# Secrets (JAMAIS commiter)
*.env
.env.local
secrets.yml

# Dépendances
node_modules/
vendor/
venv/

# Build artifacts
dist/
build/
*.exe

# IDE
.vscode/
.idea/
*.swp

# OS
.DS_Store
Thumbs.db
```

---

## 🚀 Cas d'Usage DevOps

### 1. Versioning Infrastructure as Code
```bash
# Structure Terraform
infrastructure/
├── .git/
├── environments/
│   ├── dev/
│   ├── staging/
│   └── prod/
├── modules/
└── .gitignore

# Workflow
git checkout -b feature/add-monitoring
# Modifier les fichiers Terraform
git add .
git commit -m "feat(infra): Add Prometheus monitoring"
git push origin feature/add-monitoring
# Pull Request → Review → Merge
```

### 2. GitOps (Déploiement via Git)
```yaml
# ArgoCD/FluxCD
# Git = Source of Truth
apiVersion: apps/v1
kind: Deployment
...

# Workflow
git commit → Push → ArgoCD détecte → Auto-déploie
```

### 3. Git Hooks pour Validation
```bash
# .git/hooks/pre-commit
#!/bin/sh
# Vérifier le code avant commit

# Linter
npm run lint
if [ $? -ne 0 ]; then
  echo "❌ Lint failed. Fix errors before committing."
  exit 1
fi

# Tests
npm test
if [ $? -ne 0 ]; then
  echo "❌ Tests failed. Fix tests before committing."
  exit 1
fi

echo "✅ Pre-commit checks passed"
```

---

## 📊 Exercices Pratiques

| # | Exercice | Compétences | Durée |
|---|----------|-------------|-------|
| 01 | Installation | Setup | 30min |
| 02 | Premier Repo | init, add, commit | 45min |
| 03 | Commits Atomiques | Bonnes pratiques | 1h |
| 04 | Branches | branch, checkout | 1h |
| 05 | Merge et Conflits | merge, résolution | 2h |
| 06 | Remote | clone, push, pull | 1h |
| 07 | Pull Requests | Collaboration | 1h30 |
| 08 | Git Flow | Workflow | 2h |
| 09 | GitHub Flow | Workflow | 1h30 |
| 10 | Rebase | Historique propre | 2h |
| 11 | Commandes Avancées | stash, cherry-pick | 1h30 |
| 12 | Git Hooks | Automatisation | 2h |

---

## 🎓 Ressources Complémentaires

### Documentation
- [Pro Git Book (FR)](https://git-scm.com/book/fr/v2) - Gratuit
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Learning Lab](https://lab.github.com/)

### Outils Visuels
- [GitKraken](https://www.gitkraken.com/) - Client Git graphique
- [SourceTree](https://www.sourcetreeapp.com/) - Alternative gratuite
- [Git Graph (VS Code)](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)

### Pratique Interactive
- [Learn Git Branching](https://learngitbranching.js.org/?locale=fr_FR) ⭐
- [Git Kata](https://github.com/eficode-academy/git-katas)
- [Oh My Git!](https://ohmygit.org/) - Jeu pour apprendre Git

---

## ✅ Auto-Évaluation

### Niveau Débutant
- [ ] Je comprends ce qu'est un commit
- [ ] Je sais créer un repository
- [ ] Je sais faire add/commit/push
- [ ] Je peux cloner un projet

### Niveau Intermédiaire
- [ ] Je crée et merge des branches
- [ ] Je résous les conflits
- [ ] Je fais des Pull Requests
- [ ] Je comprends Git Flow

### Niveau Avancé
- [ ] J'utilise rebase efficacement
- [ ] Je configure des hooks
- [ ] Je nettoie l'historique Git
- [ ] Je forme d'autres personnes

---

**Prochaine étape :** [CONTAINER - Docker](../CONTAINER/DOCKER/README.md) 🐳

---

*"Git is not perfect, but it's the best we have"* - Linus Torvalds
