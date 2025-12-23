# 🎮 Exercice 03 : Maîtriser kubectl

## 🎯 Objectif
Devenir fluide avec les commandes impératives pour inspecter et déboguer le cluster.

## 💡 L'Analogie : Le Couteau Suisse du Contremaître
*   **kubectl** n'est pas juste un talkie-walkie, c'est aussi vos jumelles, votre tournevis et votre carnet de notes.
*   `get` = Regarder de loin (Jumelles).
*   `describe` = Lire la fiche technique détaillée (Dossier médical).
*   `logs` = Écouter ce que le musicien raconte (Micro).
*   `exec` = Se téléporter à côté du musicien pour régler son instrument (Intervention).

## 🗺️ Roadmap & Étapes

### Étape 1 : L'Espionnage (Logs)
Votre application ne marche pas ? Écoutez-la.
1.  Lancer un pod qui parle (ex: un script qui fait des `echo`).
2.  Lire la sortie standard.
    *   *Commande* : `kubectl logs <nom-du-pod>`

### Étape 2 : L'Infiltration (Exec)
Besoin de vérifier un fichier à l'intérieur ?
1.  Ouvrir un terminal DANS le conteneur.
    *   *Commande* : `kubectl exec -it <nom-du-pod> -- /bin/sh`
    *   *Action* : Faites un `ls` ou `cat` pour vérifier les fichiers internes.

### Étape 3 : Les Raccourcis (Alias)
Un bon contremaître est rapide.
1.  Configurer l'alias `k`.
    *   *Commande* : `alias k=kubectl`
2.  Configurer l'autocomplétion.
