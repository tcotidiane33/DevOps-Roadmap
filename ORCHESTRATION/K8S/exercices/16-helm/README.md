# 📦 Exercice 16 : Helm (Package Manager)

## 🎯 Objectif
Installer des applications complexes (Prometheus, WordPress) en une seule commande, et gérer vos propres templates.

## 💡 L'Analogie : L'App Store / Le Kit IKEA
*   **Kubernetes YAML** = Construire un meuble en coupant le bois et en forgeant les vis vous-même. Long et complexe.
*   **Helm Chart** = Le **Carton IKEA**.
    *   Tout est dedans.
    *   Le fichier `values.yaml` est la **Notice de montage** personnalisable : "Je veux le meuble en rouge (image tag) avec 3 étagères (replicas)".
*   **Helm** = L'installateur qui monte le meuble pour vous.

## 🗺️ Roadmap & Étapes

### Étape 1 : Utiliser un Chart Existant
1.  Ajouter un repo (ex: Bitnami).
2.  Installer Nginx ou WordPress.
    *   *Commande* : `helm install mon-wordpress bitnami/wordpress`
    *   *Résultat* : Helm crée Deployment, Service, Secret, PVC, Ingress... tout seul.

### Étape 2 : Créer son Propre Chart
1.  Créer la structure : `helm create mon-chart`.
2.  Remplacer les valeurs "en dur" dans vos YAMLs par des `{{ .Values.image }}`.
3.  Packager et distribuer.
