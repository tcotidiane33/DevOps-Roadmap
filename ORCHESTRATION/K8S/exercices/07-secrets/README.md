# 🔒 Exercice 07 : Secrets

## 🎯 Objectif
Gérer les données sensibles (mots de passe, clés API) de manière sécurisée.

## 💡 L'Analogie : Le Coffre-Fort
*   La **ConfigMap** est un Post-it visible par tous.
*   Le **Secret** est un message dans une **enveloppe scellée** (encodée en Base64) mise dans un coffre.
*   Kubernetes s'assure que seul le robot autorisé (le Pod) a la clé pour ouvrir le coffre et lire le message au dernier moment.

## 🗺️ Roadmap & Étapes

### Étape 1 : Encodage (Base64)
Attention, Base64 n'est pas du chiffrement, c'est juste de l'emballage opaque.
1.  Encoder votre mot de passe : `echo -n "monSuperMdp" | base64`.

### Étape 2 : Créer le Secret
1.  Fichier `secret.yaml`.
2.  Type `Opaque`.
3.  Coller la valeur encodée.

### Étape 3 : Utilisation
Comme pour la ConfigMap.
1.  Injecter dans le Pod via `env` (`valueFrom: secretKeyRef`).
2.  L'application voit le mot de passe en clair, mais il n'est pas écrit en clair dans le YAML du dépôt Git (en théorie, attention aux bonnes pratiques GitOps !).
