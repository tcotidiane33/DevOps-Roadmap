# 💾 Exercice 08 : Volumes (EmptyDir & HostPath)

## 🎯 Objectif
Comprendre comment stocker des données qui survivent au crash d'un conteneur (mais pas forcément à la mort du Pod).

## 💡 L'Analogie : Le Sac à Dos et le Casier
*   **Conteneur sans volume** : Le robot a une mémoire de poisson rouge. S'il redémarre, il a tout oublié.
*   **Volume `emptyDir`** : C'est un **Sac à Dos** partagé entre les conteneurs d'un même Pod. Si le Pod meurt, le sac est brûlé avec lui. Utile pour le cache temporaire.
*   **Volume `hostPath`** : C'est un **Casier** dans le vestiaire (le Node). Si le Pod change de vestiaire (change de Node), il perd l'accès à son casier. Dangereux en production multi-nodes.

## 🗺️ Roadmap & Étapes

### Étape 1 : Le Besoin de Mémoire
1.  Lancer un Pod Redis sans volume.
2.  Écrire une donnée.
3.  Tuer le Pod.
4.  Le nouveau Pod a perdu la donnée.

### Étape 2 : Le Sac à Dos (emptyDir)
1.  Ajouter un volume `emptyDir` dans le YAML.
2.  Monter ce volume dans deux conteneurs du même Pod (ex: un qui écrit, un qui lit).
3.  Vérifier qu'ils partagent bien les fichiers.
