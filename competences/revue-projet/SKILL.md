---
name: revue-projet
description: Revue d'ensemble d'un projet, au regard extérieur, cadrée par l'humain avant de commencer. Juge comment et pourquoi le travail a été fait, pas seulement ce qui a été fait : le problème et la cible, la dette de départ, l'approche choisie face aux autres voies. Reconstitue d'abord le dossier du projet, demande par questions à choix multiple ce qu'on regarde, conteste chaque choix structurant après en avoir fait le meilleur plaidoyer, doute de ses propres conclusions et rend une page. Déclencheurs : « revue », « avis d'ensemble », « est-ce qu'on va dans la bonne direction », « recadre ce projet », « est-ce qu'on s'y prend bien », /revue-projet.
---

# Revue de projet

Tu juges un projet comme un pair extérieur juge un dossier : le problème
était-il bien posé, la voie choisie était-elle la bonne, et le travail y
mène-t-il ? Ce qui a été fait ne compte qu'à travers **comment** et
**pourquoi**. Tu recommandes ; l'humain décide.

## 1. Reconstituer le dossier (avant toute question)

Lis toi-même, sans sous-agent : le jugement se forme à la lecture. La
dernière revue de ce projet s'il y en a une, puis : le cap, les décisions
datées, l'état et la todo de chaque agent, le plan de chantier,
`git log --oneline -50` de la mémoire ; puis le code de haut en bas
(arborescence, manifeste, les plus gros fichiers) : sa forme, pas ses
bogues, qui sont l'affaire de l'audit.

Écris, une ligne chacun, ce que tu en déduis :
- **le problème** : qui souffrait de quoi, avant le projet ;
- **la cible** : ce qui sera vrai à la fin, et à quoi on le verra ;
- **le point de départ** : ce qui existait, la dette héritée ;
- **l'approche** : les trois à cinq choix dont tout le reste dépend, chacun
  avec son pourquoi écrit, ou « pas de pourquoi écrit ».

Une ligne que tu ne tires d'aucune source est déjà un constat.

## 2. Demander ce qu'on regarde

Avec l'outil de questions (AskUserQuestion), en **un seul appel** :

1. **Pourquoi maintenant** (choix unique) : recadrage général · avant une
   décision (à nommer) · ça patine · fin de phase.
2. **Ma lecture du dossier** (choix unique), les quatre lignes du § 1 dans
   la question : juste · à corriger (l'humain précise).
3. **Les angles** (choix multiples) :
   - le problème et la cible ;
   - l'approche et la dette ;
   - la trajectoire : le travail mène-t-il à la cible ?
   - l'équipe et la méthode.
4. **L'horizon** (choix unique) : la semaine · la phase en cours · le projet
   entier.

Recommande « le problème et la cible » et « l'approche et la dette » sauf
raison contraire, marqués « (Recommandé) » : c'est le cœur d'une revue. Ne
commence rien avant la réponse ; corrige le dossier selon la deuxième.

## 3. Juger

**Chaque choix que tu contestes**, dans cet ordre :
1. **Son meilleur plaidoyer** : pourquoi c'était raisonnable, avec ce qu'on
   savait alors. Une critique qui n'a pas battu ce plaidoyer ne sort pas.
2. **Les autres voies** : au moins deux réelles, dont la plus simple, écartées
   ou jamais envisagées ; pour chacune, coût, risque, délai, et ce qu'elle
   aurait changé. « Si on recommençait aujourd'hui, avec ce qu'on sait » ?
3. **Le verdict** : tient · tenait mais ne tient plus (qu'est-ce qui a
   changé) · n'était pas le bon choix ; puis ce que coûte de changer
   maintenant, face à ce que coûte de continuer.

**Par angle retenu** :
- **Le problème et la cible** : est-ce le problème de l'utilisateur ou celui
  de l'équipe ? La cible se mesure-t-elle ? Un plan réussi en entier
  résoudrait-il le problème ?
- **L'approche et la dette** : refaire ou reprendre, construire ou
  réutiliser, l'ordre des lots, les outils ; quelle dette existait, laquelle
  a été remboursée, gardée, créée, et était-ce le moment.
- **La trajectoire** : ce qui a été fait depuis deux semaines mène-t-il à la
  cible ? Qu'est-ce qui ne la sert pas ?
- **L'équipe et la méthode** : qui attend qui, qui fait deux fois la même
  chose, quelles questions restent sans réponse et depuis quand ; les
  preuves de « fait » sont-elles réelles ?

**Toujours, en dernier, l'échec imaginé** : « dans trois mois, c'est un
échec : pourquoi ? ». Trois récits, classés par probabilité × dégât, avec le
signe avant-coureur de chacun.

Tu peux contester toute décision, celle de l'humain comprise : cite-la avec
ses raisons d'alors, puis ce qui a changé ou ce qu'elle n'avait pas vu.
Contester n'est pas trancher : l'humain tranche.

## 4. Douter avant de rendre

Donne chaque point, sans ton raisonnement, à un sous-agent neuf **en Opus**
(par exception à la règle commune : un contradicteur faible ne réfute rien),
chargé de le réfuter et de plaider mieux que toi le choix de l'équipe. Un
point qu'il démonte et que tu ne peux pas défendre par une source sort de la
page.

## 5. Rendre

Une page datée dans ton dossier (`docs/revues/<projet>/<AAAA-MM-JJ>.md`) :
- **le dossier** : les quatre lignes du § 1, corrigées par l'humain ;
- **au plus cinq points**, les plus graves d'abord ; chacun : le choix en
  cause, son meilleur plaidoyer, les autres voies, ton verdict (mesuré ou
  supposé, et sa source), ta recommandation, une question fermée pour
  l'humain ;
- **l'échec imaginé** : les trois récits ;
- **ce qui tient**, avec pourquoi, et qu'il ne faut pas casser ;
- **ce que tu n'as pas pu juger**.

Aucune critique inventée : si un choix tient, dis-le et dis pourquoi.
