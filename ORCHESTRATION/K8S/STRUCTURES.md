# Structure de Répertoire Kubernetes (GitOps Ready)

Une structure organisée pour gérer des clusters Kubernetes, compatible avec les principes GitOps (ArgoCD, Flux).

## 📁 Structure Globale

```
kubernetes-platform/
├── apps/                          # Applications métier (Workloads)
│   ├── base/                      # Définitions de base (Helm/Kustomize)
│   │   ├── frontend/
│   │   ├── backend/
│   │   └── worker/
│   └── overlays/                  # Surcharges par environnement
│       ├── dev/
│       ├── staging/
│       └── production/
│
├── infrastructure/                # Composants système (Add-ons)
│   ├── base/
│   │   ├── ingress-nginx/         # Contrôleur Ingress
│   │   ├── cert-manager/          # Gestion certificats SSL
│   │   ├── prometheus-stack/      # Monitoring
│   │   ├── external-dns/          # DNS automatique
│   │   └── sealed-secrets/        # Gestion secrets chiffrés
│   └── overlays/
│       ├── dev/
│       ├── staging/
│       └── production/
│
├── clusters/                      # Définition des clusters (Point d'entrée GitOps)
│   ├── dev/
│   │   ├── apps.yaml              # ApplicationSet ou Kustomization apps
│   │   └── infrastructure.yaml    # ApplicationSet ou Kustomization infra
│   ├── staging/
│   └── production/
│
├── charts/                        # Helm Charts maison (si nécessaire)
│   ├── my-app-chart/
│   └── my-service-chart/
│
├── tools/                         # Scripts et utilitaires
│   ├── scripts/
│   │   ├── bootstrap-cluster.sh   # Script init cluster
│   │   ├── seal-secret.sh         # Helper pour sceller secrets
│   │   └── validate-manifests.sh  # Validation CI
│   └── templates/                 # Templates de nouveaux services
│
├── docs/                          # Documentation
│   ├── architecture/
│   ├── runbooks/
│   └── onboarding/
│
├── tests/                         # Tests de validation
│   ├── policies/                  # OPA Gatekeeper / Kyverno policies
│   └── e2e/                       # Tests bout en bout
│
├── Makefile                       # Raccourcis commandes
└── README.md                      # Point d'entrée
```

## 📋 Détails des Dossiers

### `apps/`
Contient les manifestes de vos applications.
- **base/** : Les fichiers YAML "purs" ou `kustomization.yaml` de base. Ne contient aucune spécificité d'environnement (pas de répliques fixes, pas d'URL de prod).
- **overlays/** : Utilise Kustomize pour modifier la base selon l'environnement (nombre de répliques, ressources CPU/RAM, variables d'environnement).

### `infrastructure/`
Contient les outils qui font tourner la plateforme.
- Sépare clairement le "métier" (apps) de la "plateforme" (infra).
- Géré souvent par une équipe "Platform" ou "SRE".

### `clusters/`
Le cœur du GitOps.
- Chaque dossier correspond à un cluster physique ou logique.
- C'est ici que l'outil GitOps (ArgoCD) pointe pour savoir quoi déployer.

### `tests/policies/`
Politiques de sécurité (Policy as Code).
- Exemple : Interdire les conteneurs root, forcer les ResourceQuotas.
