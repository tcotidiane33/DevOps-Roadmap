# 🌐 Exercice 11 : Ingress

## 🎯 Objectif
Exposer plusieurs services HTTP/HTTPS via une seule adresse IP publique et un seul LoadBalancer.

## 💡 L'Analogie : La Réceptionniste de l'Hôtel
*   **Service NodePort/LoadBalancer** = Donner une porte d'entrée dédiée à chaque chambre. Ça fait beaucoup de portes sur la façade.
*   **Ingress** = La **Réceptionniste**.
    *   Tout le monde entre par la porte principale (l'Ingress Controller).
    *   Le client demande "Je veux aller au restaurant" (`host: resto.hotel.com`) -> Elle l'envoie vers le Service Restaurant.
    *   Le client demande "Je veux aller au spa" (`path: /spa`) -> Elle l'envoie vers le Service Spa.

## 🗺️ Roadmap & Étapes

### Étape 1 : Installer le Contrôleur
L'Ingress n'est qu'une règle. Il faut un logiciel pour l'appliquer (Nginx, Traefik).
1.  Activer l'addon Minikube : `minikube addons enable ingress`.

### Étape 2 : Définir les Règles (Ingress Resource)
1.  Créer `ingress.yaml`.
2.  Définir les règles de routage :
    *   `host: mon-app.local` -> `service: frontend` port 80.

### Étape 3 : Le DNS
Pour que ça marche en local.
1.  Modifier votre `/etc/hosts`.
2.  Ajouter l'IP de Minikube (`minikube ip`) face à `mon-app.local`.
3.  Accéder via le navigateur.
