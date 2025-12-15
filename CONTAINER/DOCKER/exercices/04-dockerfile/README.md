# Exercice 04 : Dockerfile - Créer Votre Première Image

## 🎯 Objectifs

À la fin de cet exercice, vous saurez :
- ✅ Créer un Dockerfile
- ✅ Comprendre les instructions de base
- ✅ Builder une image
- ✅ Optimiser en utilisant le cache
- ✅ Tag et versionner vos images

## ⏱️ Durée Estimée
**2 heures**

## 📋 Prérequis
- Docker installé (Exercice 01 ✅)
- Comprendre les containers (Exercice 02-03 ✅)

---

## 📚 Partie 1 : Premier Dockerfile Simple

### Créer la Structure

```bash
# Créer dossier projet
mkdir my-first-image
cd my-first-image

# Créer fichier
touch Dockerfile
```

### Dockerfile Minimal

```dockerfile
# Image de base
FROM ubuntu:22.04

# Exécuter commande
RUN apt-get update && apt-get install -y curl

# Commande par défaut
CMD ["/bin/bash"]
```

### Builder l'Image

```bash
# Build
docker build -t my-ubuntu:1.0 .

# Explication:
# -t : tag (nom de l'image)
# . : contexte de build (dossier actuel)

# Voir l'image créée
docker images | grep my-ubuntu
```

### Tester

```bash
# Lancer container
docker run -it my-ubuntu:1.0

# Dans le container, tester curl
curl --version

# Sortir
exit
```

**✅ Checkpoint :** Vous avez créé et lancé votre première image !

---

## 📚 Partie 2 : Application Node.js

### Structure Projet

```bash
mkdir node-app
cd node-app
```

### Créer `package.json`

```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.0"
  }
}
```

### Créer `server.js`

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
  res.send('Hello from Docker! 🐳');
});

app.get('/health', (req, res) => {
  res.json({ status: 'OK', timestamp: new Date() });
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

### Créer Dockerfile

```dockerfile
# Image de base
FROM node:18-alpine

# Répertoire de travail
WORKDIR /app

# Copier package files
COPY package*.json ./

# Installer dépendances
RUN npm install

# Copier code source
COPY server.js ./

# Exposer port
EXPOSE 3000

# Commande de démarrage
CMD ["npm", "start"]
```

### Builder et Tester

```bash
# Build
docker build -t node-app:1.0 .

# Run avec port mapping
docker run -d -p 3000:3000 --name myapp node-app:1.0

# Tester
curl http://localhost:3000
# → "Hello from Docker! 🐳"

curl http://localhost:3000/health
# → {"status":"OK","timestamp":"..."}

# Voir logs
docker logs myapp

# Nettoyer
docker stop myapp
docker rm myapp
```

---

## 📚 Partie 3 : Optimiser avec le Cache

### ❌ Dockerfile Non-Optimisé

```dockerfile
FROM node:18-alpine
WORKDIR /app

# Tout copié en même temps
COPY . .

# Install
RUN npm install

EXPOSE 3000
CMD ["npm", "start"]
```

**Problème :** Chaque modification de code → Rebuild TOUT (npm install inclus)

### ✅ Dockerfile Optimisé

```dockerfile
FROM node:18-alpine
WORKDIR /app

# 1. Copier SEULEMENT package files
COPY package*.json ./

# 2. Installer dépendances (cache layer)
RUN npm ci --only=production

# 3. Copier code source (après)
COPY server.js ./

EXPOSE 3000
CMD ["npm", "start"]
```

**Avantage :** 
- Modification de `server.js` → Utilise cache npm (rapide)
- Modification de `package.json` → Rebuild npm (normal)

### Test de Performance

```bash
# Premier build
time docker build -t node-app:optimized .
# ⏱️ ~30 secondes

# Modifier server.js (changer message)
echo "// comment" >> server.js

# Rebuild
time docker build -t node-app:optimized .
# ⏱️ ~5 secondes (cache utilisé!)
```

---

## 📚 Partie 4 : Instructions Avancées

### ENV : Variables d'Environnement

```dockerfile
FROM node:18-alpine
WORKDIR /app

# Définir variables
ENV NODE_ENV=production
ENV PORT=3000
ENV DEBUG=false

COPY package*.json ./
RUN npm ci --only=production
COPY server.js ./

EXPOSE ${PORT}

CMD ["npm", "start"]
```

**Utilisation :**
```bash
# Override au runtime
docker run -e PORT=4000 -e DEBUG=true -p 4000:4000 node-app
```

### ARG : Arguments de Build

```dockerfile
FROM node:18-alpine

# Argument de build
ARG NODE_VERSION=18

WORKDIR /app

# Utiliser ARG
RUN echo "Building with Node.js ${NODE_VERSION}"

COPY package*.json ./
RUN npm ci --only=production
COPY server.js ./

EXPOSE 3000
CMD ["npm", "start"]
```

**Utilisation :**
```bash
# Passer argument au build
docker build --build-arg NODE_VERSION=20 -t node-app:node20 .
```

### USER : Sécurité (non-root)

```dockerfile
FROM node:18-alpine
WORKDIR /app

# Créer user non-root
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

COPY --chown=nodejs:nodejs package*.json ./
RUN npm ci --only=production

COPY --chown=nodejs:nodejs server.js ./

# Changer vers user nodejs
USER nodejs

EXPOSE 3000
CMD ["npm", "start"]
```

**Test :**
```bash
docker build -t node-app:secure .
docker run -d -p 3000:3000 node-app:secure

# Vérifier user
docker exec $(docker ps -ql) whoami
# → nodejs (pas root ✅)
```

---

## 📚 Partie 5 : Multi-Instructions

### LABEL : Métadonnées

```dockerfile
FROM node:18-alpine

LABEL maintainer="votre@email.com"
LABEL version="1.0"
LABEL description="My Node.js application"

WORKDIR /app
# ...
```

### HEALTHCHECK : Santé du Container

```dockerfile
FROM node:18-alpine
WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production
COPY server.js ./

EXPOSE 3000

# Health check (toutes les 30s)
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node -e "require('http').get('http://localhost:3000/health', (r) => process.exit(r.statusCode === 200 ? 0 : 1))"

CMD ["npm", "start"]
```

**Test :**
```bash
docker run -d -p 3000:3000 --name healthy node-app:health

# Voir santé
docker ps
# STATUS: healthy

docker inspect healthy --format='{{.State.Health.Status}}'
# → healthy
```

---

## 📚 Partie 6 : .dockerignore

### Créer .dockerignore

```
# Dépendances
node_modules/
npm-debug.log

# Git
.git/
.gitignore

# IDE
.vscode/
.idea/

# Tests
tests/
*.test.js

# Documentation
README.md
docs/

# Fichiers système
.DS_Store
Thumbs.db
```

**Avantage :** Build plus rapide (moins de fichiers copiés)

---

## 📚 Partie 7 : Tags et Versions

### Stratégie de Tagging

```bash
# Version spécifique
docker build -t node-app:1.0.0 .
docker build -t node-app:1.0 .
docker build -t node-app:1 .

# Latest
docker build -t node-app:latest .

# Avec SHA git
GIT_SHA=$(git rev-parse --short HEAD)
docker build -t node-app:${GIT_SHA} .

# Multiples tags en une commande
docker build -t node-app:1.0.0 -t node-app:latest .
```

### Lister toutes les images

```bash
docker images node-app

# REPOSITORY   TAG       IMAGE ID       SIZE
# node-app     1.0.0     abc123         150MB
# node-app     latest    abc123         150MB
# node-app     abc123    abc123         150MB
```

---

## ✅ Exercices Pratiques

### Exercice 1 : Application Python

Créer une app Flask :

**app.py :**
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello from Python Docker!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

**requirements.txt :**
```
Flask==2.3.0
```

**Créer Dockerfile pour cette app**

<details>
<summary>Solution</summary>

```dockerfile
FROM python:3.11-alpine
WORKDIR /app
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py ./
EXPOSE 5000
CMD ["python", "app.py"]
```

```bash
docker build -t python-app .
docker run -d -p 5000:5000 python-app
curl http://localhost:5000
```
</details>

### Exercice 2 : Optimisation

Comparer taille image :
- `FROM node:18` vs `FROM node:18-alpine`
- Avec et sans `--only=production`

### Exercice 3 : Multi-Tags

Builder une image avec 3 tags différents en une commande.

---

## 🐛 Troubleshooting

### Erreur : "failed to compute cache key"

```bash
# Cause: Fichier COPY inexistant
# Solution: Vérifier chemins fichiers
ls -la
```

### Erreur : "Cannot connect to Docker daemon"

```bash
# Solution: Démarrer Docker Desktop
# Ou vérifier service docker (Linux)
sudo systemctl start docker
```

## 🎓 Ce Que Vous Avez Appris

- ✅ Syntaxe Dockerfile
- ✅ Instructions essentielles (FROM, COPY, RUN, CMD)
- ✅ Optimisation avec cache layers
- ✅ Variables (ENV, ARG)
- ✅ Sécurité (USER)
- ✅ Health checks
- ✅ Tagging et versioning

---

## ➡️ Prochaine Étape

[Exercice 05 : Application Node.js Complète](../05-nodejs-app/README.md)

---

## 📚 Ressources

- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
