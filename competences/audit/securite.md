# Audit — section Sécurité

l'humain a choisi cette section (ou l'a nommée : « vérifie la sécurité », « on revoit la sécurité », une faille, un secret, une fuite de données, Stripe, le RGPD). Tu ne lances rien avant d'avoir compris ce qu'il veut.

| Volet | Expert (sous-agent, Fable) | Ce qu'il regarde |
|---|---|---|
| Code et paiements | `securite-code` | les failles du code web, mobile et des fonctions Edge (injections, contrôle d'accès, secrets dans le code ou l |
| Base et règles d'accès | `securite-base` | les règles par ligne de chaque table, les fonctions à privilèges (SECURITY DEFINER, search_path), les clés exp |
| Dépendances | `securite-dependances` | les paquets et leurs versions  |
| Données personnelles | `securite-rgpd` | ce que le projet collecte, pourquoi, où ça part (Sentry, Stripe, analytics), le consentement et les cookies, la s |

## 1. Comprendre — un seul appel à `AskUserQuestion`, quatre questions

1. **« Quels volets de la section Sécurité ? »** — `multiSelect: true` :
   - « Code et paiements »
   - « Base et règles d'accès »
   - « Dépendances »
   - « Données personnelles »
2. **« Pourquoi maintenant ? »** — un seul choix : « Audit complet de la section » · « Avant une livraison précise » · « Un doute précis » · « Avant un jalon (lancement, envoi en store) ». S'il en choisit un précis, sa réponse libre dit lequel.
3. **« Combien d'experts Fable au plus ? »** — un seul choix : « 1 — le plus important d'abord » · « 2 » · « Tous les volets cochés ». Rappelle dans la question qu'un expert Fable consomme beaucoup de quota.
4. **« Sur quoi ? »** — `multiSelect: true` :
   - « le web »
   - « le mobile »
   - « la base et ses fonctions »
   - « les paiements »

Il peut toujours répondre en texte libre (« Autre ») : c'est souvent là qu'il dit ce qu'il veut vraiment.

**Si `AskUserQuestion` n'est pas disponible** (session à distance qui ne l'affiche pas, refus), pose les mêmes quatre questions dans ton message de fin de tour, voies numérotées, et précise qu'il peut répondre par plusieurs chiffres (« 1, 3 »). Rien ne part avant sa réponse.

## 2. Cadrer
Mesure l'arbre (`git -C code rev-parse --abbrev-ref HEAD` et le commit) et ouvre la campagne comme d'habitude : `docs/audit/<AAAA-MM-JJ>-securite/_BRIEF.md` — ce qu'on cherche (ses réponses), sur quoi on ne conclura pas, l'arbre mesuré.

## 3. Lancer
Un appel `Agent` par volet coché, avec `subagent_type` = le nom de l'expert, tous dans le même message pour qu'ils tournent en parallèle, **jamais plus que le nombre qu'il a choisi**. Plus de volets cochés que d'experts accordés : lance les plus importants pour son « pourquoi », et dis lesquels attendent. Chaque mission porte : le pourquoi, le périmètre, l'arbre, le chemin du brief, et ce que l'humain a accordé (images, volume).

## 4. Rendre
- Chaque retour devient `<VOLET>.md` dans la campagne.
- Tu juges : un item **bloquant** se rejoue par toi avant d'entrer dans la synthèse (un expert qui annonce a annoncé). Sévérité redescendue après vérification : c'est un résultat, à écrire.
- `SYNTHESE.md` puis les plans par lot, comme toute campagne, et la BACKLOG comme d'habitude.
- À l'humain : combien d'items bloquent, ce qui est vérifié bon / vérifié mauvais / pas mesuré, et les volets non lancés.

Les experts tournent en Fable : exception à la règle commune des sous-agents, accordée par l'humain pour l'audit.
