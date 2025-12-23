# ⚖️ Exercice 14 : Requests & Limits

## 🎯 Objectif
Garantir que chaque application a assez de CPU/RAM et empêcher une application gourmande de tuer les autres.

## 💡 L'Analogie : Le Budget et le Plafond
*   **Requests** = Le **Salaire Minimum Garanti**.
    *   Kubernetes promet : "Je ne te placerai sur un Node que si je suis sûr qu'il te reste au moins ça".
*   **Limits** = Le **Plafond de Dépenses**.
    *   Si tu essaies de dépenser plus que ça (RAM), le vigile (OOMKiller) t'abat sur le champ.
    *   Si tu essaies d'utiliser plus que ça (CPU), on te ralentit (Throttling).

## 🗺️ Roadmap & Étapes

### Étape 1 : Sans Limites (Le Danger)
1.  Lancer un Pod sans resources.
2.  S'il a un bug (memory leak), il peut consommer toute la RAM du Node et faire planter le Node entier.

### Étape 2 : Définir le Contrat
1.  Ajouter `resources` dans le YAML.
2.  `requests`: 64Mi RAM, 250m CPU (0.25 cœur).
3.  `limits`: 128Mi RAM, 500m CPU.

### Étape 3 : Le Stress Test
1.  Utiliser un outil de stress pour dépasser 128Mi de RAM.
2.  Observer le Pod passer en statut `OOMKilled` (Out Of Memory).
