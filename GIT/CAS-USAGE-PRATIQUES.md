# 🎯 Cas d'Usage Pratiques Git

## 💡 Niveaux de Complexité

- 🟢 **Niveau 1** : Débutant (1-7 jours d'expérience)
- 🟡 **Niveau 2** : Intermédiaire (1-4 semaines d'expérience)
- 🔴 **Niveau 3** : Avancé (1+ mois d'expérience)

---

## 🟢 Niveau 1 : Cas Débutant

### Cas 1 : Premier Projet Personnel - Site Web Portfolio

**Contexte :** Vous créez un site web portfolio et voulez versionner votre code.

**Architecture :**
```
portfolio/
├── index.html
├── style.css
├── script.js
└── images/
    └── profile.jpg
```

**Workflow Git :**
```bash
# 1. Initialiser le projet
mkdir portfolio
cd portfolio
git init

# 2. Créer structure de base
touch index.html style.css script.js
mkdir images

# 3. Premier commit (structure)
git add .
git commit -m "Initial commit: Project structure"

# 4. Développer index.html
# ... éditer index.html
git add index.html
git commit -m "feat: Add HTML structure"

# 5. Ajouter styles
# ... éditer style.css
git add style.css
git commit -m "style: Add CSS styling"

# 6. Ajouter JavaScript
# ... éditer script.js
git add script.js
git commit -m "feat: Add navigation functionality"

# 7. Push vers GitHub
git remote add origin https://github.com/username/portfolio.git
git push -u origin main

# 8. Déployer sur GitHub Pages
git checkout -b gh-pages
git push origin gh-pages
```

**Compétences Apprises :**
- ✅ `git init`
- ✅ `git add` et `git commit`
- ✅ Messages de commit conventionnels
- ✅ Remote repository
- ✅ GitHub Pages deployment

**Temps estimé :** 2 heures

---

### Cas 2 : Corriger une Erreur - Annuler un Commit

**Contexte :** Vous avez commis un fichier par erreur (mot de passe dans config.js).

**Scénario :**
```bash
# Situation initiale
git add config.js
git commit -m "Add config"
# ❌ Oups! config.js contient des secrets

# Solution 1: Annuler le dernier commit (garde changements)
git reset --soft HEAD~1
# Éditer config.js pour retirer secrets
git add config.js
git commit -m "Add config (without secrets)"

# Solution 2: Modifier le dernier commit
git commit --amend -m "Add config (corrected)"

# Solution 3: Si déjà pushé (créer nouveau commit)
# Éditer config.js
git add config.js
git commit -m "fix: Remove secrets from config"
git push
```

**Compétences Apprises :**
- ✅ `git reset --soft`
- ✅ `git commit --amend`
- ✅ Bonnes pratiques sécurité
- ✅ Utilisation de `.gitignore`

**Temps estimé :** 30 minutes

---

### Cas 3 : Collaboration Simple - Projet Scolaire

**Contexte :** Vous travaillez à 2 sur un projet de groupe.

**Workflow :**
```bash
# Personne A: Créer le repo
git init
git remote add origin https://github.com/team/projet.git
git push -u origin main

# Personne B: Cloner
git clone https://github.com/team/projet.git
cd projet

# Personne A: Travailler sur header
git checkout -b feature/header
# ... créer header.html
git add header.html
git commit -m "feat: Add header"
git push origin feature/header

# Personne B: Travailler sur footer
git checkout -b feature/footer
# ... créer footer.html
git add footer.html
git commit -m "feat: Add footer"
git push origin feature/footer

# Sur GitHub: Créer Pull Requests
# Review mutuellement
# Merger dans main

# Personne A et B: Récupérer les changements
git checkout main
git pull origin main
```

**Compétences Apprises :**
- ✅ `git clone`
- ✅ Branches pour features
- ✅ Pull Requests
- ✅ Code review
- ✅ `git pull` pour synchroniser

**Temps estimé :** 3 heures

---

## 🟡 Niveau 2 : Cas Intermédiaire

### Cas 4 : Résoudre un Conflit de Merge

**Contexte :** Deux développeurs modifient le même fichier.

**Scénario :**
```bash
# Dev A et Dev B travaillent sur main

# Dev A: Modifie style.css
git checkout main
echo "color: blue;" >> style.css
git commit -am "style: Blue theme"
git push

# Dev B: Modifie aussi style.css (sans pull d'abord)
echo "color: red;" >> style.css
git commit -am "style: Red theme"
git push  # ❌ Rejeté! Besoin de pull d'abord

# Dev B: Pull → CONFLIT
git pull origin main

# Auto-merging style.css
# CONFLICT (content): Merge conflict in style.css

# Ouvrir style.css:
# <<<<<<< HEAD
# color: red;
# =======
# color: blue;
# >>>>>>> origin/main

# Résoudre (choisir une couleur ou combiner)
# Éditer style.css
color: purple;  # Compromis

# Marquer comme résolu
git add style.css
git commit -m "merge: Resolve color conflict (use purple)"
git push
```

**Compétences Apprises :**
- ✅ Comprendre les conflits
- ✅ Résolution manuelle
- ✅ Communication en équipe
- ✅ `git merge`

**Temps estimé :** 2 heures

---

### Cas 5 : Feature Branch Workflow - Application Web

**Contexte :** Développement d'une app avec plusieurs features en parallèle.

**Architecture :**
```
app/
├── frontend/
├── backend/
├── docs/
└── tests/
```

**Workflow :**
```bash
# Structure Git Flow
main          # Production
develop       # Intégration
feature/*     # Nouvelles features

# 1. Créer develop
git checkout -b develop main

# 2. Feature: User Authentication
git checkout -b feature/user-auth develop
# ... développer auth
git add .
git commit -m "feat(auth): Add user registration"
git commit -m "feat(auth): Add login endpoint"
git commit -m "test(auth): Add auth tests"

# 3. Merge feature dans develop
git checkout develop
git merge feature/user-auth
git branch -d feature/user-auth

# 4. Feature parallèle: Search
git checkout -b feature/search develop
# ... développer search
git commit -m "feat(search): Add search functionality"

# 5. Release vers production
git checkout -b release/v1.0 develop
# ... tests finaux, corrections
git commit -m "chore: Bump version to 1.0"

# 6. Merger release dans main
git checkout main
git merge release/v1.0
git tag v1.0

# 7. Merger aussi dans develop
git checkout develop
git merge release/v1.0
```

**Compétences Apprises :**
- ✅ Git Flow complet
- ✅ Gestion de releases
- ✅ Tags pour versions
- ✅ Branches de long terme vs éphémères

**Temps estimé :** 1 semaine (projet complet)

---

### Cas 6 : Hotfix Urgent en Production

**Contexte :** Bug critique découvert en production, besoin de fix immédiat.

**Scénario :**
```bash
# Production (main) : v1.0
# Develop : Plein de nouvelles features en cours

# 1. Créer hotfix depuis main
git checkout main
git checkout -b hotfix/security-patch

# 2. Fixer le bug
# ... corriger le problème de sécurité
git add .
git commit -m "fix(security): Patch XSS vulnerability"

# 3. Tester le fix
npm test

# 4. Merger dans main
git checkout main
git merge hotfix/security-patch
git tag v1.0.1

# 5. Déployer IMMÉDIATEMENT
git push origin main --tags

# 6. Merger aussi dans develop (important!)
git checkout develop
git merge hotfix/security-patch

# 7. Nettoyer
git branch -d hotfix/security-patch
```

**Compétences Apprises :**
- ✅ Hotfix workflow
- ✅ Gestion d'urgence
- ✅ Tags de version
- ✅ Double merge (main + develop)

**Temps estimé :** 2-3 heures

---

## 🔴 Niveau 3 : Cas Avancé

### Cas 7 : Contribution Open Source

**Contexte :** Contribuer à un projet open source sur GitHub.

**Workflow Complet :**
```bash
# 1. Fork le projet sur GitHub (interface web)

# 2. Cloner VOTRE fork
git clone https://github.com/VOUS/projet-opensource.git
cd projet-opensource

# 3. Ajouter upstream (repo original)
git remote add upstream https://github.com/ORIGINAL/projet-opensource.git

# 4. Créer branche feature
git checkout -b fix/typo-in-docs

# 5. Faire les changements
# ... corriger typo dans README
git add README.md
git commit -m "docs: Fix typo in installation section"

# 6. Push vers VOTRE fork
git push origin fix/typo-in-docs

# 7. Créer Pull Request sur GitHub
# Interface web → "New Pull Request"
# Remplir description détaillée

# 8. Pendant review: Rester à jour avec upstream
git fetch upstream
git rebase upstream/main

# 9. S'il y a des demandes de changements
# ... faire modifications
git add .
git commit -m "docs: Address review comments"
git push origin fix/typo-in-docs

# 10. Une fois merged: Nettoyer
git checkout main
git pull upstream main
git push origin main
git branch -d fix/typo-in-docs
```

**Compétences Apprises :**
- ✅ Fork workflow
- ✅ Upstream synchronization
- ✅ Rebase pour clean history
- ✅ PR best practices

**Temps estimé :** 4-6 heures (première fois)

---

### Cas 8 : Rebase Interactif - Nettoyer Historique

**Contexte :** Vous avez fait 10 commits brouillons, besoin de nettoyer avant PR.

**Scénario :**
```bash
# Historique désordonné:
git log --oneline
abc123 - WIP
def456 - fix typo
ghi789 - actually implement feature
jkl012 - oops forgot file
mno345 - remove debug logs
pqr678 - final implementation

# Nettoyer avec rebase interactif (6 derniers commits)
git rebase -i HEAD~6

# Éditeur s'ouvre:
pick abc123 WIP
squash def456 fix typo
squash ghi789 actually implement feature
squash jkl012 oops forgot file
squash mno345 remove debug logs
pick pqr678 final implementation

# Sauvegarder → Nouveau message de commit
# Résultat propre:
feat: Implement user authentication

- Add login endpoint
- Add registration endpoint
- Add password hashing
- Add JWT tokens

# Force push (⚠️ seulement si branche pas partagée)
git push -f origin feature/auth
```

**Compétences Apprises :**
- ✅ `git rebase -i`
- ✅ Squash commits
- ✅ Réécriture d'historique
- ✅ Force push (et dangers)

**Temps estimé :** 1-2 heures

---

### Cas 9 : Monorepo - Plusieurs Projets dans un Repo

**Contexte :** Gérer frontend, backend, mobile dans un seul repository.

**Structure :**
```
monorepo/
├── packages/
│   ├── web/
│   ├── api/
│   ├── mobile/
│   └── shared/
├── .gitignore
└── lerna.json (ou pnpm-workspace.yaml)
```

**Workflow :**
```bash
# 1. Structure branches par package
git checkout -b feature/web-dashboard
# Travailler dans packages/web/
git commit -m "feat(web): Add dashboard"

git checkout -b feature/api-users
# Travailler dans packages/api/
git commit -m "feat(api): Add users endpoint"

# 2. .gitignore intelligent
packages/*/node_modules
packages/*/dist
*.log

# 3. Commits scope par package
git commit -m "feat(web): Add dashboard"
git commit -m "fix(api): Resolve DB connection"
git commit -m "feat(mobile): Add login screen"
git commit -m "refactor(shared): Extract common utils"

# 4. Releases par package
git tag web-v1.0.0
git tag api-v2.3.1
git tag mobile-v1.1.0
```

**Compétences Apprises :**
- ✅ Monorepo structure
- ✅ Scoped commits
- ✅ Multiple tags
- ✅ Workspace management

**Temps estimé :** Setup 4h + ongoing

---

### Cas 10 : Git Hooks pour CI/CD Local

**Contexte :** Automatiser checks avant chaque commit/push.

**Setup :**
```bash
# 1. Créer pre-commit hook
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/sh

echo "🔍 Running pre-commit checks..."

# Lint
npm run lint
if [ $? -ne 0 ]; then
  echo "❌ Lint failed"
  exit 1
fi

# Format check
npm run format:check
if [ $? -ne 0 ]; then
  echo "❌ Format check failed"
  exit 1
fi

# Unit tests
npm test
if [ $? -ne 0 ]; then
  echo "❌ Tests failed"
  exit 1
fi

echo "✅ All pre-commit checks passed"
exit 0
EOF

chmod +x .git/hooks/pre-commit

# 2. Créer pre-push hook
cat > .git/hooks/pre-push << 'EOF'
#!/bin/sh

echo "🚀 Running pre-push checks..."

# Integration tests
npm run test:integration
if [ $? -ne 0 ]; then
  echo "❌ Integration tests failed"
  exit 1
fi

# Build check
npm run build
if [ $? -ne 0 ]; then
  echo "❌ Build failed"
  exit 1
fi

echo "✅ All pre-push checks passed"
exit 0
EOF

chmod +x .git/hooks/pre-push

# 3. Commit msg validation
cat > .git/hooks/commit-msg << 'EOF'
#!/bin/sh

commit_msg_file=$1
commit_msg=$(cat "$commit_msg_file")

# Valider format: type(scope): message
if ! echo "$commit_msg" | grep -qE "^(feat|fix|docs|style|refactor|test|chore)(\(.+\))?: .+"; then
  echo "❌ Invalid commit message format"
  echo "Expected: type(scope): message"
  echo "Example: feat(auth): Add login"
  exit 1
fi

echo "✅ Commit message valid"
exit 0
EOF

chmod +x .git/hooks/commit-msg
```

**Utilisation :**
```bash
# Maintenant chaque commit déclenche:
git commit -m "test"
# 🔍 Running pre-commit checks...
# → lint → format → tests → ✅

# Chaque push déclenche:
git push
# 🚀 Running pre-push checks...
# → integration tests → build → ✅
```

**Compétences Apprises :**
- ✅ Git hooks
- ✅ Automatisation locale
- ✅ Quality gates
- ✅ Shell scripting

**Temps estimé :** 3 heures setup

---

## 📊 Tableau Récapitulatif

| Cas | Niveau | Compétences Clés | Use Case | Temps |
|-----|--------|------------------|----------|-------|
| 1 | 🟢 | init, commit, push | Portfolio | 2h |
| 2 | 🟢 | reset, amend | Corriger erreur | 30min |
| 3 | 🟢 | clone, branches, PR | Projet groupe | 3h |
| 4 | 🟡 | merge conflicts | Collaboration | 2h |
| 5 | 🟡 | Git Flow | App web | 1 semaine |
| 6 | 🟡 | hotfix, tags | Bug production | 2-3h |
| 7 | 🔴 | fork, upstream | Open source | 4-6h |
| 8 | 🔴 | rebase -i | Clean history | 1-2h |
| 9 | 🔴 | monorepo | Multi-packages | 4h+ |
| 10 | 🔴 | hooks | Automation | 3h |

---

## 🎯 Progression Recommandée

**Semaine 1 :** Cas 1, 2  
**Semaine 2 :** Cas 3, 4  
**Semaine 3 :** Cas 5, 6  
**Semaine 4+ :** Cas 7, 8, 9, 10

---

**Prochaine étape :** [Retour au Parcours Pédagogique](./PARCOURS-PEDAGOGIQUE.md)
