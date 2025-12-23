# 📞 Exercice 05 : Services & Networking

## 🎯 Objectif
Exposer vos applications pour qu'elles puissent communiquer entre elles ou avec l'extérieur.

## 💡 L'Analogie : Le Standard Téléphonique
*   Les Pods sont comme des employés mobiles : ils changent de bureau (d'IP) tout le temps. Impossible de les appeler directement.
*   **Le Service** = Le **Numéro Unique** du département (ex: "Service Compta").
    *   Quand vous appelez le Service Compta, le standard redirige l'appel vers un comptable disponible au hasard.
    *   Peu importe si le comptable a changé de bureau ce matin, le numéro du Service reste le même.

## 🗺️ Roadmap & Étapes

### Étape 1 : Le Besoin (Pourquoi ?)
1.  Lancez un Deployment.
2.  Essayez de contacter un Pod par son IP.
3.  Tuez le Pod. Le nouveau a une nouvelle IP. Votre lien est cassé.

### Étape 2 : La Solution Interne (ClusterIP)
Pour que le Backend parle à la Database.
1.  Créer un Service de type `ClusterIP`.
2.  Le Selector doit matcher les labels des Pods.
    *   *Résultat* : Une IP stable interne au cluster.

### Étape 3 : L'Ouverture vers l'Extérieur (NodePort / LoadBalancer)
Pour que les clients accèdent au Frontend.
1.  Créer un Service de type `NodePort`.
2.  Accéder à l'app via `IP_DU_NODE:PORT`.
    *   *Analogie* : Percer un trou dans le mur du bâtiment pour passer un câble vers l'extérieur.
