# 🏆 Exercice 18 : Projet Final

## 🎯 Objectif
Mettre en œuvre toutes les compétences acquises pour déployer une architecture micro-services complète et production-ready.

## 💡 L'Analogie : L'Examen de Maîtrise
Vous n'êtes plus un apprenti qui pose des briques isolées. Vous êtes maintenant le **Chef de Chantier** qui livre un immeuble clé en main.

## 🗺️ Roadmap & Étapes

### Étape 1 : L'Architecture
Déployer une application "E-commerce" composée de :
1.  **Frontend** (React/Vue) exposé via Ingress.
2.  **Backend** (Node/Go) accessible uniquement par le Frontend.
3.  **Database** (Postgres/Mongo) avec persistance (PVC) et mot de passe sécurisé (Secret).
4.  **Cache** (Redis) pour la performance.

### Étape 2 : Les Bonnes Pratiques
1.  **Health Checks** : Liveness et Readiness probes configurées.
2.  **Resources** : Requests et Limits définies pour tous les pods.
3.  **Config** : Variables d'environnement sorties dans des ConfigMaps.
4.  **Sécurité** : NetworkPolicies pour isoler la DB.

### Étape 3 : L'Automatisation
1.  Packager le tout dans un **Helm Chart**.
2.  Déployer via **ArgoCD**.
3.  Mettre en place un **HPA** sur le Frontend.

Félicitations, vous êtes un ingénieur Kubernetes ! 🎓
