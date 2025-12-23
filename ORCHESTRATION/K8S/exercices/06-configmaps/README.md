# ⚙️ Exercice 06 : ConfigMaps

## 🎯 Objectif
Séparer la configuration du code de l'application.

## 💡 L'Analogie : Les Post-it sur le Frigo
*   Votre application est comme un **robot cuisinier**.
*   Le code (l'image Docker) est son **logiciel interne** (il sait couper, cuire, mélanger).
*   La **ConfigMap** est le **Post-it** que vous collez sur son front pour lui dire *quoi* cuisiner aujourd'hui.
    *   "Menu = Pizza"
    *   "Couleur de la nappe = Rouge"
*   Si vous voulez changer le menu, vous changez juste le Post-it (ConfigMap), vous ne reconstruisez pas le robot (Image).

## 🗺️ Roadmap & Étapes

### Étape 1 : Créer le Post-it (ConfigMap)
1.  Créer un fichier YAML `configmap.yaml`.
2.  Y mettre des données clé-valeur (ex: `DATABASE_URL: postgres://...`).

### Étape 2 : Coller le Post-it sur le Robot (Pod)
1.  Dans le `deployment.yaml`, référencer la ConfigMap.
2.  Soit comme **Variables d'Environnement** (`envFrom`).
3.  Soit comme **Fichier** monté dans un volume.

### Étape 3 : Vérifier
1.  Entrer dans le pod (`kubectl exec`).
2.  Vérifier que les variables sont là (`env` ou `cat /etc/config/fichier`).
