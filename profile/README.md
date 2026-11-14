# Agenteca

Un catalogue et un gestionnaire d'agents IA, « façon HACS » : installez et tenez à jour des agents, des skills, des commandes, des hooks et des serveurs MCP depuis des dépôts git, dans **Claude Code**, **Codex**, **GitHub Copilot** et **Cursor**.

```bash
ahub add propriétaire/dépôt
```

Agenteca n'invente pas de format : les paquets suivent **OpenAPM** (`apm.yml`, `apm.lock.yaml`), les skills le standard **Agent Skills**, les serveurs d'outils **MCP**. Ce que le projet apporte, c'est le catalogue, l'interface, les intégrations et la gestion des droits.

Un agent est du texte exécuté par un modèle : Agenteca le traite comme du code. Chaque paquet est scanné, et tout ce qui sera écrit vous est montré avant de l'être.

## Dépôts

| Dépôt | Rôle | Licence |
|---|---|---|
| [agenteca-core](https://github.com/agenteca/agenteca-core) | Bibliothèque : manifeste, résolution, lockfile, adaptateurs, scan | Apache-2.0 |
| [agenteca-cli](https://github.com/agenteca/agenteca-cli) | La commande `ahub` et son contrat JSON | Apache-2.0 |
| [agenteca-server](https://github.com/agenteca/agenteca-server) | API REST et index du catalogue | AGPL-3.0 |
| [agenteca-web](https://github.com/agenteca/agenteca-web) | Site du catalogue | AGPL-3.0 |
| [agenteca-mcp](https://github.com/agenteca/agenteca-mcp) | Serveur MCP | Apache-2.0 |
| [agenteca-claude-code](https://github.com/agenteca/agenteca-claude-code) | Plugin Claude Code | Apache-2.0 |
| [agenteca-codex](https://github.com/agenteca/agenteca-codex) | Plugin Codex | Apache-2.0 |
| [agenteca-copilot](https://github.com/agenteca/agenteca-copilot) | Plugin GitHub Copilot CLI | Apache-2.0 |
| [agenteca-vscode](https://github.com/agenteca/agenteca-vscode) | Extension VS Code (Cursor et dérivés via Open VSX) | Apache-2.0 |
| [agenteca-jetbrains](https://github.com/agenteca/agenteca-jetbrains) | Plugin JetBrains | Apache-2.0 |
| [agenteca-registry](https://github.com/agenteca/agenteca-registry) | Catalogue de départ et paquet d'exemple | Apache-2.0 |
| agenteca-ee | Fonctions premium (squelette) | Propriétaire |

## Comment tout s'articule

Toutes les intégrations sont des coques fines au-dessus de la CLI : elles appellent `ahub --json` et n'ont aucune logique d'installation propre. Le comportement est donc le même partout.

```
extensions IDE ─┐
plugins d'agents ─→ agenteca-mcp ─┐
                                  ├─→ ahub (agenteca-cli) ─→ agenteca-core
site web ─→ agenteca-server ──────┘
```

Deux contrats versionnés relient les dépôts : le schéma JSON de la sortie de `ahub`, et la spécification OpenAPI du serveur.

## Modèle open core

Le cœur est libre. La gestion fine des droits (SSO, SCIM, rôles personnalisés, droits par équipe, audit, validation avant publication) est une couche premium séparée, que le serveur charge si elle est installée et dont il se passe sinon.

## Contribuer

Voir [CONTRIBUTING.md](https://github.com/agenteca/.github/blob/main/CONTRIBUTING.md). Pour une faille de sécurité, voir [SECURITY.md](https://github.com/agenteca/.github/blob/main/SECURITY.md).
