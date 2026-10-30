---
name: audit-code
description: Audit de code d'un projet, cadré par l'humain avant de commencer. Demande d'abord, par questions à choix multiple, le but de l'audit, les dimensions à couvrir et le périmètre ; puis lance un sous-agent neuf par dimension choisie (trois au plus à la fois), vérifie chaque constat, et rend un seul rapport avec un plan de corrections par lot. Déclencheurs : « audit », « audite le code », « pourquoi l'app est refusée », « tout ce qui peut casser », /audit-code.
---

# Audit de code

Tu trouves ce qui ne marche pas, ou pourrait ne pas marcher, dans le code
d'un projet. Tu ne corriges rien : tu prescris, l'équipe du projet corrige.

## 1. S'orienter (avant toute question)

Lis le README, le manifeste (`package.json`, `pyproject.toml`, `app.json`…),
les décisions du projet, et `git log --oneline -100`. Repère le type de projet
(app mobile, web, données, service) et les 20 fichiers les plus gros et les
plus modifiés : la dette s'y cache. Écris en trois lignes ce que tu as compris.

## 2. Demander ce qu'on audite

Avec l'outil de questions (AskUserQuestion), en **un seul appel** :

1. **Le but** (choix unique) : passer une revue de store (App Store, Play) ·
   avant une mise en production · réduire la dette · sécurité d'abord.
2. **Ce qui casse** (choix multiples) : bogues et plantages · tests ·
   performance · erreurs et journaux.
3. **Ce qui coûte et ce qui expose** (choix multiples) : architecture et
   dette · dépendances et configuration · sécurité et données personnelles ·
   conformité au store ou à la plateforme.
4. **Le périmètre** (choix unique) : tout le dépôt · un module (à nommer) ·
   les changements depuis une date · un parcours d'utilisateur (à nommer).

Recommande une sélection selon le but, en la marquant « (Recommandé) ». Ne
lance rien avant la réponse.

## 3. Auditer, dimension par dimension

Un **sous-agent neuf par dimension choisie**, **trois au plus à la fois**.
Chacun reçoit : le périmètre, la grille de sa dimension (ci-dessous), la règle
« chaque constat cite `fichier:ligne` et la commande ou la lecture qui le
montre ; aucun constat sans preuve ». Ils lisent, ils n'écrivent rien.

| Dimension | Ce qu'on cherche |
|---|---|
| Bogues et plantages | chemins qui lèvent une exception non rattrapée, valeurs nulles, courses, états impossibles, démarrage à froid, hors ligne, petits et grands écrans |
| Tests | chemins critiques sans test, tests qui vérifient l'implémentation et pas le comportement, tests sautés ou instables |
| Performance | requêtes en boucle, travail bloquant sur un chemin chaud, fuites (écouteurs, minuteries), rendus inutiles |
| Erreurs et journaux | exceptions avalées, `catch` fourre-tout, erreurs journalisées mais non traitées, rien de journalisé sur un chemin critique |
| Architecture et dette | fichiers ou fonctions géants, logique dupliquée en trois endroits, code mort, couches qui se contournent, plusieurs façons de faire la même chose |
| Dépendances et configuration | failles connues (`npm audit`, `pip-audit`), dépendances inutiles ou en double, variables d'environnement non documentées, versions incohérentes |
| Sécurité et données personnelles | secrets en dur, SQL par concaténation, entrées non validées, droits trop larges, données personnelles journalisées ou envoyées sans besoin |
| Conformité store / plateforme | voir § 4 |

## 4. Si c'est une app mobile soumise à un store

Ce qui fait refuser une app, à vérifier dans le code et la configuration :
- **plantage ou écran vide** au lancement, sur iPad aussi (le relecteur teste
  souvent sur iPad), hors ligne, et en build de **production** (pas seulement
  en développement) ;
- **fonction cassée** : lien mort, bouton sans effet, contenu de test,
  compte de démonstration absent pour la relecture ;
- **autorisations** : chaque usage (caméra, position, photos, suivi) a son
  texte d'explication ; rien n'est demandé sans besoin ;
- **confidentialité** : manifeste de confidentialité, déclarations de
  collecte cohérentes avec ce que le code envoie, suppression de compte si
  création de compte ;
- **achats** : biens numériques par l'achat intégré du store ;
- **React Native** : écarts entre build de dev et de production, modules
  natifs mal liés, promesses rejetées sans traitement, `console.log` laissés,
  versions de React Native et des bibliothèques natives compatibles.

Les règles des stores changent : vérifie chaque point contre leur version du
jour avant de l'affirmer. Lis aussi le savoir-faire `ios` ou `android` s'il
est branché.

## 5. Vérifier, puis rendre

Relis toi-même la ligne citée de chaque constat **bloquant** ou **majeur** ;
un constat qui ne tient pas à la relecture sort du rapport. Fusionne les
doublons entre dimensions.

Le rapport, daté, dans ton dossier (`docs/audits/<projet>/<AAAA-MM-JJ>.md`) :
- en tête : le but, les dimensions couvertes, le nombre de bloquants ;
- chaque constat : `### [bloquant|majeur|mineur] <en une ligne>`, puis
  **Où**, **Preuve**, **Attendu**, **Correction**, **Vérifier** ;
- **a l'air mauvais mais tient** : ce qu'il ne faut pas « corriger » ;
- **pas audité** : les dimensions écartées et ce que tu n'as pas pu lire ;
- **plan par lot** : les corrections regroupées pour l'agent qui les fera,
  que l'humain transmet.

Jamais de « tout réécrire » : la plus petite correction qui tient.
