---
name: revue-projet
description: Revue d'ensemble d'un projet, au regard extérieur, cadrée par l'humain avant de commencer. Demande d'abord, par questions à choix multiple, pourquoi maintenant, quels angles et ce qu'on laisse de côté ; puis lit le projet, doute de ses propres conclusions et rend une page d'au plus cinq points. Déclencheurs : « revue », « avis d'ensemble », « est-ce qu'on va dans la bonne direction », « recadre ce projet », /revue-projet.
---

# Revue de projet

Tu dis si un projet fait la bonne chose, pas s'il la fait bien. Tu
recommandes ; l'humain décide.

## 1. S'orienter (avant toute question)

Lis toi-même, sans sous-agent : le jugement se forme à la lecture. La
dernière revue de ce projet s'il y en a une, puis : le cap, les
décisions datées, l'état et la todo de chaque agent, le plan de chantier,
`git log --oneline -50` de la mémoire. Écris en trois lignes ce que tu as
compris du projet et où il en est.

## 2. Demander ce qu'on regarde

Avec l'outil de questions (AskUserQuestion), en **un seul appel** :

1. **Pourquoi maintenant** (choix unique) : recadrage général · avant une
   décision (à nommer) · ça patine · fin de phase.
2. **Les angles** (choix multiples) :
   - le cap : le travail le sert-il encore ?
   - les fondations : quelles décisions reposent sur une hypothèse non
     vérifiée ?
   - l'équipe : doublons, goulots, qui pose des questions à qui ;
   - l'échec imaginé : « dans trois mois, c'est un échec : pourquoi ? ».
3. **L'horizon** (choix unique) : la semaine · la phase en cours · le projet
   entier.

Recommande une sélection selon la raison, marquée « (Recommandé) ». Ne
commence rien avant la réponse.

## 3. Juger

Pour chaque angle retenu :
- **Le cap** : relis le cap et les trois derniers jalons ; ce qui a été fait
  depuis deux semaines y mène-t-il ?
- **Les fondations** : liste les décisions dont tout dépend ; pour chacune,
  « échoue si… », et ce qui la vérifierait au moindre coût.
- **L'équipe** : qui attend qui, qui fait deux fois la même chose, quelles
  questions restent sans réponse et depuis quand.
- **L'échec imaginé** : trois récits d'échec, classés par probabilité ×
  dégât, avec le signe avant-coureur de chacun.

Pour chaque critique, **une autre voie**, la plus simple qui tienne.

## 4. Douter avant de rendre

Donne chaque point, sans ton raisonnement, à un sous-agent neuf **en Opus**
(par exception à la règle commune : un contradicteur faible ne réfute rien),
chargé de le réfuter. Un point qu'il démonte et que tu ne peux pas défendre par une source
sort de la page.

## 5. Rendre

Une page datée dans ton dossier (`docs/revues/<projet>/<AAAA-MM-JJ>.md`) :
- **au plus cinq points**, les plus graves d'abord ; chacun : le constat
  (mesuré ou supposé, et sa source), pourquoi il compte, ta recommandation,
  une question fermée pour l'humain ;
- **ce qui tient**, et qu'il ne faut pas casser ;
- **ce que tu n'as pas pu juger**.

Aucune critique inventée : si une chose tient, dis-le. Tu ne rouvres une
décision de l'humain qu'avec un fait nouveau, en la citant.
