# 👑 Exercice 10 : StatefulSets

## 🎯 Objectif
Gérer des applications à état (Bases de données) où l'identité et l'ordre des Pods comptent.

## 💡 L'Analogie : Les Sièges Numérotés
*   **Deployment** = Une foule anonyme. Les Pods s'appellent `web-xh54z`, `web-9j2kl`. Ils sont interchangeables. Comme des spectateurs en fosse.
*   **StatefulSet** = Des VIP avec places attitrées. Les Pods s'appellent `db-0`, `db-1`, `db-2`.
    *   `db-0` est le Chef (Master).
    *   `db-1` ne démarre que quand `db-0` est prêt.
    *   Si `db-0` meurt, il revient en s'appelant toujours `db-0` et retrouve ses données personnelles (son PVC attitré).

## 🗺️ Roadmap & Étapes

### Étape 1 : La Différence
1.  Créer un StatefulSet `web`.
2.  Observer les noms : `web-0`, `web-1`.
3.  Tuer `web-0`. Il revient en tant que `web-0` (pas `web-z8f4s`).

### Étape 2 : Le Stockage Dédié (VolumeClaimTemplates)
La magie du StatefulSet.
1.  Ajouter `volumeClaimTemplates` au YAML.
2.  Chaque réplique reçoit son PROPRE disque dur unique (`data-web-0`, `data-web-1`).
3.  C'est crucial pour les bases de données (Master/Slave).
