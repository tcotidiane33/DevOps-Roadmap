# 🛡️ Exercice 12 : Network Policies

## 🎯 Objectif
Contrôler quel Pod a le droit de parler à quel autre Pod (Firewall interne).

## 💡 L'Analogie : Les Badges de Sécurité
*   Par défaut, dans K8s, c'est **Open Bar**. Tout le monde peut parler à tout le monde. Le stagiaire (Pod Frontend) peut accéder directement au coffre-fort (Pod Database).
*   **NetworkPolicy** = Le système de **Badges**.
    *   "Seuls les employés du service 'Backend' ont le droit d'entrer dans le bureau 'Database'".
    *   "Interdit de sortir du bâtiment (Internet) sauf pour le service 'Météo'".

## 🗺️ Roadmap & Étapes

### Étape 1 : Le Constat (Open Bar)
1.  Lancer un Pod `hacker` dans un namespace différent.
2.  Vérifier qu'il peut pinger votre Database. (Spoiler: Oui).

### Étape 2 : Le Verrouillage (Deny All)
La bonne pratique de sécurité.
1.  Créer une Policy qui interdit tout trafic entrant (`ingress: []`) sur la Database.
2.  Vérifier que plus personne ne passe.

### Étape 3 : L'Ouverture Ciblée (Allow Backend)
1.  Modifier la Policy.
2.  Autoriser seulement les Pods avec le label `app: backend`.
3.  Vérifier que le Backend passe, mais pas le Hacker.
