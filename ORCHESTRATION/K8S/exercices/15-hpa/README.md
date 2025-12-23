# 📈 Exercice 15 : Horizontal Pod Autoscaler (HPA)

## 🎯 Objectif
Ajuster automatiquement le nombre de répliques selon la charge (CPU/RAM).

## 💡 L'Analogie : Le Recrutement d'Intérimaires
*   **HPA** = Le **DRH Automatique**.
    *   Il regarde la sueur des employés (CPU %).
    *   Si la moyenne de sueur dépasse 50%, il appelle l'agence d'intérim pour ajouter un clone (Scale Up).
    *   Si tout le monde se tourne les pouces (< 50%), il renvoie les intérimaires chez eux (Scale Down).

## 🗺️ Roadmap & Étapes

### Étape 1 : Pré-requis (Metrics Server)
Le DRH a besoin de thermomètres.
1.  Activer `metrics-server` sur Minikube.
    *   *Commande* : `minikube addons enable metrics-server`

### Étape 2 : Définir les Règles (HPA)
1.  Avoir un Deployment avec des `requests` CPU définies (obligatoire !).
2.  Créer un HPA : "Cible = 50% CPU, Min = 1, Max = 10".
    *   *Commande* : `kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10`

### Étape 3 : La Charge
1.  Générer du trafic artificiel (boucle `while true; wget ...`).
2.  Observer le nombre de pods augmenter (`kubectl get hpa -w`).
3.  Arrêter le trafic et voir le nombre redescendre.
