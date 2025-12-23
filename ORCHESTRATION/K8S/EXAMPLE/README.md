# Plateforme Kubernetes (Exemple GitOps)

Ce répertoire contient un exemple de structure pour gérer des clusters Kubernetes selon les principes GitOps.

## Organisation

- **apps/** : Définitions des applications (Workloads). Utilise Kustomize pour gérer les variantes (dev/staging/prod).
- **infrastructure/** : Composants système (Ingress, Cert-Manager, Monitoring).
- **clusters/** : Point d'entrée pour ArgoCD/Flux. Chaque dossier représente un environnement cible.

## Comment ça marche ?

1.  **Base** : Les manifestes communs sont dans `apps/base/`.
2.  **Overlays** : Les spécificités (répliques, images, config) sont dans `apps/overlays/`.
3.  **Déploiement** : ArgoCD surveille le dossier `clusters/dev` et applique les changements détectés dans `apps/overlays/dev`.

## Exemple Inclus

- **Frontend** : Une application Nginx simple définie dans `apps/base/frontend`.
- **Dev Overlay** : Une surcharge pour l'environnement de dev dans `apps/overlays/dev` (1 réplique).
- **ArgoCD App** : La définition de l'application ArgoCD dans `clusters/dev/apps.yaml`.
