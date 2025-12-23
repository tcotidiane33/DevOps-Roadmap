# 📦 Exercice 02 : Votre Premier Pod

## 🎯 Objectif
Lancer votre toute première application dans Kubernetes sous forme de Pod.

## 💡 L'Analogie : Le Musicien Solitaire
*   **Le Pod** = C'est un **musicien** avec son instrument.
*   **Le Conteneur** = C'est l'**instrument** (le piano).
*   **Kubernetes** = La scène.
*   *Note* : Dans K8s, on ne gère pas les instruments (conteneurs) directement, on gère les musiciens (Pods) qui en jouent.

## 🗺️ Roadmap & Étapes

### Étape 1 : Écrire la Partition (Manifeste YAML)
On décrit qui doit jouer.
1.  Créer un fichier `pod.yaml`.
2.  Définir `kind: Pod`.
3.  Choisir l'image (l'instrument), par exemple `nginx`.

### Étape 2 : Faire Monter sur Scène (Apply)
On envoie le musicien sur scène.
1.  Appliquer le fichier.
    *   *Commande* : `kubectl apply -f pod.yaml`

### Étape 3 : Vérifier le Spectacle (Get/Describe)
On regarde si le musicien joue bien.
1.  Lister les pods.
    *   *Commande* : `kubectl get pods`
    *   *Attendu* : Status `Running`.
2.  Voir les détails (s'il a un problème).
    *   *Commande* : `kubectl describe pod mon-premier-pod`

### Étape 4 : Le Renvoyer en Coulisse (Delete)
Le spectacle est fini.
1.  Supprimer le pod.
    *   *Commande* : `kubectl delete pod mon-premier-pod`
