# 🐙 Exercice 17 : ArgoCD (GitOps)

## 🎯 Objectif
Déployer des applications automatiquement depuis Git, sans jamais faire de `kubectl apply` manuel.

## 💡 L'Analogie : Le Pilote Automatique
*   **Méthode Manuelle** = Vous conduisez la voiture. Si vous dormez, la voiture sort de la route.
*   **GitOps (ArgoCD)** = Le **Pilote Automatique**.
    *   Vous entrez la destination dans le GPS (Git).
    *   La voiture (ArgoCD) tourne le volant pour rester sur la route (Cluster).
    *   Si quelqu'un donne un coup de volant (modification manuelle du cluster), le pilote automatique corrige immédiatement la trajectoire pour revenir au plan GPS (Self-Healing).

## 🗺️ Roadmap & Étapes

### Étape 1 : Installer ArgoCD
1.  Créer le namespace `argocd`.
2.  Appliquer le manifeste d'installation officiel.

### Étape 2 : Connecter au Git
1.  Accéder à l'UI d'ArgoCD (via Port-Forward).
2.  Créer une "Application".
3.  Source = Votre repo Git.
4.  Destination = Votre cluster local.

### Étape 3 : La Synchro
1.  Cliquer sur "Sync".
2.  Modifier un fichier dans Git (changer le nombre de replicas).
3.  Voir ArgoCD détecter le changement et mettre à jour le cluster tout seul.
