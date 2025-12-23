# 🚀 Exercice 04 : Deployments & ReplicaSets

## 🎯 Objectif
Gérer plusieurs copies d'une application et les mettre à jour sans interruption.

## 💡 L'Analogie : Le Chef de Section et ses Clones
*   **Le Pod** = Un soldat. Il est mortel. S'il meurt, il ne revient pas.
*   **Le Deployment** = Le **Général**. Il donne un ordre : "Je veux 3 soldats de type Nginx en permanence sur le terrain".
*   **Le ReplicaSet** = Le **Sergent recruteur**. Il vérifie en permanence l'effectif. S'il compte 2 soldats au lieu de 3, il en clone un nouveau immédiatement. S'il en compte 4, il en élimine un.

## 🗺️ Roadmap & Étapes

### Étape 1 : L'Ordre de Mission (Créer le Deployment)
Au lieu de créer un Pod, on crée un Deployment.
1.  Fichier `deployment.yaml`.
2.  Spécifier `replicas: 3`.
3.  Appliquer.
    *   *Résultat* : 3 Pods apparaissent (`kubectl get pods`).

### Étape 2 : Le Test de Résilience (Tuer un Pod)
Prouver que le Sergent fait son travail.
1.  Supprimer un des 3 pods manuellement.
    *   *Commande* : `kubectl delete pod <nom-un-pod>`
2.  Observer la magie.
    *   *Commande* : `kubectl get pods -w`
    *   *Résultat* : Un nouveau pod est créé instantanément pour revenir à 3.

### Étape 3 : La Mise à Jour (Rolling Update)
Changer l'équipement des soldats sans arrêter la guerre.
1.  Modifier l'image dans le YAML (passer de `nginx:1.14` à `nginx:latest`).
2.  Appliquer.
    *   *Résultat* : K8s remplace les pods un par un. Zéro coupure de service.
