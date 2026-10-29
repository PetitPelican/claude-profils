# Profils d'agent — la bibliothèque des métiers

Un **profil** est un métier qu'on donne à un agent, indépendamment du projet :
ce qu'il fait, sa méthode, ses limites, les savoir-faire qu'il charge et ses
réglages. Le **projet** reste ce qui le rend concret : le code, la marque, les
clients, les règles maison. Un agent reçoit les deux : un profil générique et
le `CLAUDE.md` de son projet.

Les fiches sont tirées d'agents en service, puis rendues génériques.

**Monter tout un atelier sur une machine neuve** — l'ordre, les deux familles
d'agents, comment un agent de projet consulte un expert, les droits de chacun
et les commandes : [`METHODE.md`](METHODE.md).

## Les profils

**DEV** : un agent de projet, qui possède un lot. **Expert** : un agent
transverse, qui sert l'atelier ou plusieurs projets (`METHODE.md`, § 2).

| Profil | Famille | Métier | Modèle |
|---|---|---|---|
| [`ops`](ops.md) | DEV | DevOps : backend, infrastructure, mise en Production | Sonnet |
| [`po`](po.md) | DEV | développeur et Product Owner : le produit et les applications | Sonnet |
| [`qa`](qa.md) | DEV | qualité, audits, plans et pilotage de l'équipe | Opus |
| [`dev`](dev.md) | DEV | un produit construit seul, de la base aux écrans (PO + OPS) | Opus |
| [`bi`](bi.md) | DEV | tableaux de bord, chemin des données | Opus |
| [`cto`](cto.md) | Expert | la machine, les agents et les communs | Opus |
| [`harness`](harness.md) | Expert | le paquet du harnais | Opus |
| [`designer`](designer.md) | Expert | identité, interfaces, supports, données | Opus |
| [`juriste`](juriste.md) | Expert | droit français et européen d'une société | Opus |
| [`comptable`](comptable.md) | Expert | comptabilité et fiscalité d'une société | Opus |
| [`hacker`](hacker.md) | Expert | sécurité offensive, en lecture | Opus |
| [`archi`](archi.md) | Expert | architecture des données : modèle, chemin, qualité, accès | Opus |
| [`steward`](steward.md) | Expert | le regard extérieur sur un projet : cap, fondations, équipe, risques | Fable |

## Comment une fiche est faite

**Une fiche EST le `CLAUDE.md` du métier** : le texte sous l'en-tête est ce que
l'agent lit comme consigne (expertise, méthode, frontières). Elle ne s'appelle
pas `CLAUDE.md` parce qu'elle n'est jamais recopiée : le `CLAUDE.md` de
l'agent l'importe par une ligne (`@~/Agentic/claude-profils/<profil>.md`), puis
n'ajoute que ce qui est propre à son projet. Sans cette ligne, l'agent ne
reçoit que les savoir-faire et le modèle.

Un en-tête, puis le rôle en texte :

```yaml
---
profil: designer            # le nom qu'on passe à la commande
titre: Designer             # ce que l'humain lit
modele: opus[1m]            # posé à chaque relance de l'agent
effort: high
competences:                # chemins sous ~/.claude-competences/, rafraîchis chaque lundi
  - corey-haines/skills/copywriting
env:                        # variables ajoutées aux réglages de l'agent
  HARNAIS_PROFIL: expert
---
```

Les savoir-faire **communs à tous** (visualisation de données, design
d'interface, tests, ceux de la stack de vos projets…) vivent dans
`~/.claude/skills/` : une fiche ne liste que ceux qui sont propres à son
métier.

## D'où viennent les savoir-faire

Tous vivent dans `~/.claude-competences/`, un exemplaire par dépôt, rafraîchi
chaque semaine. Choisis en octobre 2026 après lecture
intégrale de chaque fiche, au plus 10 par profil.

| Dépôt | Étoiles (14/10) | Licence | Profils |
|---|---|---|---|
| `obra/superpowers` | 299 k | MIT | ops, po, qa, dev, cto, harness, steward |
| `addyosmani/agent-skills` | 107 k | MIT | ops, po, qa, dev, hacker, cto, harness, steward |
| `wshobson/agents` | 41 k | MIT | ops, hacker, archi |
| `anthropics/knowledge-work-plugins` | 30 k | Apache-2.0 | po, dev, archi, steward |
| `ancoleman/ai-design-components` | 525 (27/10) | MIT | archi (`architecting-data` seule ; dernier envoi le 10/12/2025) |
| `trailofbits/skills` | 7,5 k | CC-BY-SA-4.0 | hacker |
| `coreyhaines31/marketingskills` | 55 k | MIT | designer |
| `ehmo/platform-design-skills` | 625 (26/10) | MIT | designer (la fiche iPad seule, `ipados`) |
| `romainsimon/paperasse` | — | — | comptable |
| `Tough-Respawn/legal-skills-france` | — | MIT | juriste |

**Écartés après lecture** (ne pas rebrancher sans relire) : `ci-cd-and-automation`
(commits, déploiements et fusions automatiques), `spec-driven-development` (arrêt
à chaque phase, fichier de tâches concurrent), `idea-refine` (script, sorties
dans `docs/`), `browser-testing-with-devtools` (serveur à télécharger),
`doubt-driven-development` (sous-agents en boucle, envoi du code à des services
tiers), `incremental-implementation` (un commit par tranche),
`incident-runbook-templates` (commandes de production étrangères à l'atelier),
l'extension `claude-security` d'Anthropic (jusqu'à des centaines de sous-agents
par analyse, `git` pré-autorisé), `feature-dev` et `pr-review-toolkit`
(sous-agents en parallèle à chaque étape) ; chez Trail of Bits, `differential-review` (bascule l'arbre de travail par `git checkout`), `audit-context-building` (un sous-agent par fonction), `entry-point-analyzer` et `agentic-actions-auditor` (hors du web et du mobile). Pour `archi` (27/10) : `data-quality-frameworks` de wshobson (fiche tronquée en son milieu, et elle fait installer Great Expectations), les fiches de `ancoleman` qui livrent des scripts (`using-relational-databases`, `transforming-data`, `ingesting-data`), et `dbt-labs/dbt-agent-skills` (747 ★, Apache-2.0, sérieux) **tant qu'aucun projet n'utilise dbt** — à brancher le jour où un projet l'adopte. `supply-chain-risk-auditor` est gardé : il envoie les NOMS des dépendances à des registres publics, jamais le code ni les constats.

Les consignes de l'atelier passent avant celles d'un savoir-faire.

## Appliquer un profil

Trois gestes, dans le dossier de l'agent :

1. **les savoir-faire** : un lien par entrée de `competences:` dans
   `.claude/skills/` (`ln -s ~/.claude-competences/<chemin> .claude/skills/`) ;
2. **le modèle et l'effort** : ceux de l'en-tête, au lancement de l'agent ;
3. **le rôle** (facultatif) : la ligne `@~/Agentic/claude-profils/<profil>.md`
   en tête de son `CLAUDE.md`, et les `env:` dans son `.claude/settings.json`.

Sans le rôle, l'agent garde le sien et reçoit seulement les outils du métier.
Avec, la fiche est **importée**, pas recopiée : une correction ici arrive chez
tous les agents qui la portent, à leur prochain démarrage. Un outil de poste
peut faire les trois d'un coup.

Tout prend effet au **prochain démarrage** de l'agent.

## Règles de la bibliothèque

0. **Un profil ajoute, il ne retire jamais.** Un agent a souvent un périmètre
   plus large que son nom. Appliqué à un agent en place, un profil lui donne
   des savoir-faire de plus, jamais une frontière de plus : on n'importe pas
   la fiche chez un agent qui a déjà son rôle, sauf demande de l'humain.
1. **Rien de propre à un projet** : ni nom de client, ni chemin, ni marque, ni
   chiffre. Ce qui ne vaudrait que pour un projet va dans le `CLAUDE.md` de ce
   projet.
2. **Rien qui identifie quelqu'un, ni un projet, ni sa stack** : le dépôt est
   public.
3. Une fiche se corrige ici, jamais dans la copie d'un agent.
