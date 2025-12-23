# 👮 Exercice 13 : RBAC (Role Based Access Control)

## 🎯 Objectif
Gérer les permissions des utilisateurs et des applications vis-à-vis de l'API Kubernetes.

## 💡 L'Analogie : Le Permis de Construire
*   **User/ServiceAccount** = L'**Identité** (Qui êtes-vous ?). "Je suis Bob".
*   **Role** = Le **Permis** (Qu'avez-vous le droit de faire ?). "Droit de lire les plans (get pods) mais pas de casser les murs (delete pods)".
*   **RoleBinding** = La **Signature du Contrat**. "On donne le Permis 'Architecte' à 'Bob' pour le chantier 'Dev'".

## 🗺️ Roadmap & Étapes

### Étape 1 : Créer l'Identité (ServiceAccount)
Pour une application (ex: un bot CI/CD).
1.  Créer un ServiceAccount `mon-bot`.

### Étape 2 : Définir les Droits (Role)
1.  Créer un Role `pod-reader`.
2.  Verbes autorisés : `get`, `list`, `watch`.
3.  Ressources : `pods`.

### Étape 3 : Lier les deux (RoleBinding)
1.  Créer un RoleBinding qui lie `mon-bot` à `pod-reader`.

### Étape 4 : Vérifier (Auth Can-I)
1.  Demander à K8s : "Est-ce que je peux supprimer des pods en tant que mon-bot ?"
    *   *Commande* : `kubectl auth can-i delete pods --as=system:serviceaccount:default:mon-bot`
    *   *Réponse* : `no`.
