# Contribuer à Agenteca

Merci de votre intérêt. Ce document vaut pour tous les dépôts de l'organisation.

## Avant de coder

- Pour un bogue : ouvrez un ticket dans le dépôt concerné, avec de quoi le reproduire.
- Pour une fonctionnalité : ouvrez d'abord un ticket pour en discuter.
- Pour une faille de sécurité : **pas de ticket public**, voir [SECURITY.md](SECURITY.md).

## Principe directeur : réutiliser les standards

Agenteca n'invente un format que si aucun standard ne couvre le besoin. Avant de proposer un nouveau fichier ou un nouveau champ, vérifiez OpenAPM, Agent Skills, AGENTS.md, MCP, SemVer, SPDX, OpenAPI et SARIF. Si aucun ne convient, expliquez pourquoi dans la demande.

Les formats des outils changent vite : appuyez-vous sur leur documentation officielle du moment, citez-la, et écrivez « non confirmé » plutôt que de deviner.

## Où va le code

Les intégrations (extensions IDE, plugins, serveur MCP) sont des coques fines au-dessus de `ahub --json`. Toute logique d'installation, de résolution ou de sécurité va dans `agenteca-core` ou `agenteca-cli`, jamais dans une intégration.

## Les deux contrats

| Contrat | Fichier | Règle |
|---|---|---|
| Sortie de `ahub --json` | `agenteca-cli/schemas/cli-output.v1.schema.json` | Ajouter un champ : version mineure. Retirer un champ ou en changer le sens : version majeure. |
| API du serveur | `agenteca-server/openapi.json` | Généré depuis le code (`npm run openapi`) ; même règle. |

Une demande qui touche à un contrat le dit dans sa description et met à jour le `CHANGELOG.md`.

## Sécurité : règles non négociables

- Rien n'est exécuté à l'installation d'un paquet.
- Rien n'est écrit sans avoir été montré.
- Un fichier modifié à la main n'est jamais écrasé ni supprimé sans accord explicite.
- Une intégration pilotée par un modèle ne peut pas contourner le scan.
- Une fonction non implémentée échoue visiblement ; elle ne prétend jamais protéger.

## Qualité

- Chaque changement de comportement vient avec un test.
- `npm run lint`, `npm run typecheck` et `npm test` passent (pour le plugin JetBrains : `./gradlew check`).
- Commits petits et atomiques, messages à l'impératif : `feat: …`, `fix: …`, `docs: …`, `test: …`, `chore: …`.
- Chaque dépôt suit SemVer et tient un `CHANGELOG.md`.

## Développer en local

Les dépôts se développent côte à côte, dans un même dossier, reliés par un espace de travail npm (un `package.json` à la racine listant les dépôts dans `workspaces`). Chaque dépôt déclare ses dépendances vers les autres en versions normales (`^0.1.0`).

## Accord de contribution

| Dépôts | Ce qui est demandé |
|---|---|
| Sous Apache-2.0 | **DCO** : signez chaque commit avec `git commit -s`. Voir [DCO.md](DCO.md). |
| `agenteca-server`, `agenteca-web` (AGPL-3.0), `agenteca-ee` | **CLA** : voir [CLA.md](CLA.md). |

Pourquoi un CLA pour le serveur et le site : ils sont sous AGPL, et le module premium, propriétaire, s'y branche. Seul le titulaire des droits peut combiner les deux ; il lui faut donc des droits suffisants sur chaque contribution.

## Code de conduite

La participation au projet est soumise au [code de conduite](CODE_OF_CONDUCT.md).
