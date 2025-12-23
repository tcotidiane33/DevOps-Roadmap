# 🏁 Exercice 01 : Installation & Setup

## 🎯 Objectif
Installer un cluster Kubernetes local (Minikube ou Kind) et configurer l'outil de commande `kubectl`.

## 💡 L'Analogie : Le Chantier et le Contremaître
*   **Le Cluster (Minikube)** = C'est votre **terrain de construction** clôturé. C'est là que tout va se passer.
*   **kubectl** = C'est votre **talkie-walkie** pour donner des ordres aux ouvriers sur le terrain. Sans lui, vous pouvez crier, personne ne vous entendra.

## 🗺️ Roadmap & Étapes

### Étape 1 : Installer le Moteur (Docker)
Avant de créer le terrain, il faut que le sol soit prêt.
1.  Assurez-vous que Docker Desktop est lancé.
    *   *Commande* : `docker ps` (ne doit pas renvoyer d'erreur).

### Étape 2 : Créer le Terrain (Minikube/Kind)
On délimite la zone de travaux.
1.  Installer Minikube (ou Kind).
2.  Démarrer le cluster.
    *   *Commande* : `minikube start`
    *   *Résultat* : Une machine virtuelle ou un conteneur se lance pour simuler un cluster complet.

### Étape 3 : Prendre le Talkie-Walkie (kubectl)
On vérifie que la communication passe.
1.  Vérifier la version client/serveur.
    *   *Commande* : `kubectl version`
2.  Demander "Qui est là ?".
    *   *Commande* : `kubectl get nodes`
    *   *Attendu* : Vous devez voir un "node" (votre machine) prêt à travailler (`Ready`).
