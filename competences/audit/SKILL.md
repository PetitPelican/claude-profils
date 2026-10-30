---
name: audit
description: Lancer un audit du projet avec les experts de QA. À charger dès que l'humain dit « lance un audit », « je veux un audit », « audite … », ou nomme une des cinq sections (sécurité, fiabilité, qualité, stores, architecture). Demande d'abord la section, puis pose les questions de cette section, et ne lance que les experts choisis, en Fable.
---

# Audit

Cinq sections, chacune avec ses experts (sous-agents en Fable) :

1. **Sécurité** — code et paiements, base et règles d'accès, dépendances, données personnelles → `securite.md`
2. **Fiabilité** — une livraison, relecture du code, tests et alertes, cohérence des données → `fiabilite.md`
3. **Qualité** — performance du web et du mobile, accessibilité, interface → `qualite.md`
4. **Stores** — règles Apple et Google, technique de l'envoi, fiche de store, essai sur simulateur → `stores.md`
5. **Architecture** — modèle de données, structure du code, dette et mises à jour → `architecture.md`

## 1. La section
Si l'humain l'a déjà nommée, passe à l'étape 2. Sinon, demande-la dans ton message de fin de tour, voies numérotées 1 à 5 comme ci-dessus (une ligne par section, avec ce qu'elle regarde) : il répond par un chiffre. Rien d'autre dans ce message.

## 2. Les questions de la section
Lis le fichier de la section choisie, dans ce dossier, et suis-le : il pose ses questions à choix multiples (volets, pourquoi, combien d'experts Fable, sur quoi), puis cadre, lance et rend.

Les experts tournent en Fable : exception à la règle commune des sous-agents, accordée par l'humain pour l'audit.
