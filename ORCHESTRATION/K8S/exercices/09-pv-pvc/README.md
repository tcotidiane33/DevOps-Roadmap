# 🗄️ Exercice 09 : Persistent Volumes (PV) & Claims (PVC)

## 🎯 Objectif
Stocker des données de manière durable, indépendamment du cycle de vie des Pods et des Nodes.

## 💡 L'Analogie : Le Ticket de Vestiaire Universel
*   **StorageClass** = Le **Service de Location** d'entrepôts (AWS EBS, Google Disk, NFS).
*   **PersistentVolumeClaim (PVC)** = Votre **Ticket de Demande**. "Je veux 10Go de stockage rapide".
*   **PersistentVolume (PV)** = L'**Entrepôt réel** qui vous est attribué.
*   **Le Pod** = Le locataire. Il arrive avec son ticket (PVC), et Kubernetes lui connecte automatiquement le bon entrepôt (PV), peu importe où il habite.

## 🗺️ Roadmap & Étapes

### Étape 1 : La Demande (PVC)
Le développeur ne se soucie pas de la marque du disque dur.
1.  Créer un `pvc.yaml`.
2.  Demander 1Gi en `ReadWriteOnce`.

### Étape 2 : L'Attribution (Binding)
1.  Appliquer le PVC.
2.  Observer : Si une StorageClass par défaut existe, un PV est créé automatiquement ("Dynamic Provisioning") et lié (`Bound`) à votre PVC.

### Étape 3 : L'Utilisation
1.  Dans le Pod, référencer le PVC par son nom dans `volumes`.
2.  Les données écrites ici survivront même si vous supprimez le Pod et le recréez ailleurs.
