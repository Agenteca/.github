# Agenteca

A catalog and manager of AI agents, in the spirit of HACS: install and keep up to date agents, skills, commands, hooks and MCP servers from git repositories, in **Claude Code**, **Codex**, **GitHub Copilot** and **Cursor**.

```bash
ahub add owner/repo
```

Agenteca invents no format: packages follow **OpenAPM** (`apm.yml`, `apm.lock.yaml`), skills follow the **Agent Skills** standard, tool servers follow **MCP**. What the project brings is the catalog, the interface, the integrations and the management of rights.

An agent is text executed by a model: Agenteca treats it as code. Every package is scanned, and everything that will be written is shown to you before it is.

The command line, the web site and the editor extensions speak English, French, Spanish, Chinese and Hindi.

## Repositories

| Repository | Purpose | License |
|---|---|---|
| [agenteca-core](https://github.com/agenteca/agenteca-core) | Library: manifest, resolution, lockfile, adapters, scan | Apache-2.0 |
| [agenteca-cli](https://github.com/agenteca/agenteca-cli) | The `ahub` command and its JSON contract | Apache-2.0 |
| [agenteca-server](https://github.com/agenteca/agenteca-server) | REST API and catalog index | AGPL-3.0 |
| [agenteca-web](https://github.com/agenteca/agenteca-web) | Catalog web site | AGPL-3.0 |
| [agenteca-mcp](https://github.com/agenteca/agenteca-mcp) | MCP server | Apache-2.0 |
| [agenteca-claude-code](https://github.com/agenteca/agenteca-claude-code) | Claude Code plugin | Apache-2.0 |
| [agenteca-codex](https://github.com/agenteca/agenteca-codex) | Codex plugin | Apache-2.0 |
| [agenteca-copilot](https://github.com/agenteca/agenteca-copilot) | GitHub Copilot CLI plugin | Apache-2.0 |
| [agenteca-vscode](https://github.com/agenteca/agenteca-vscode) | VS Code extension (Cursor and derivatives through Open VSX) | Apache-2.0 |
| [agenteca-jetbrains](https://github.com/agenteca/agenteca-jetbrains) | JetBrains plugin | Apache-2.0 |
| [agenteca-registry](https://github.com/agenteca/agenteca-registry) | Starter catalog and example package | Apache-2.0 |
| [agenteca-agents](https://github.com/agenteca/agenteca-agents) | First agents of the catalog: a kit for building multi-repository open-source projects | Apache-2.0 |
| agenteca-ee | Premium features (skeleton) | Proprietary |

## How it fits together

Every integration is a thin shell over the CLI: it calls `ahub --json` and has no installation logic of its own. Behaviour is therefore the same everywhere.

```
IDE extensions ──┐
agent plugins ──→ agenteca-mcp ──┐
                                 ├─→ ahub (agenteca-cli) ─→ agenteca-core
web site ─→ agenteca-server ─────┘
```

Two versioned contracts link the repositories: the JSON schema of the output of `ahub`, and the OpenAPI specification of the server.

## Open-core model

The core is free. Fine-grained rights management (SSO, SCIM, custom roles, per-team rights, audit, validation before publication) is a separate premium layer, which the server loads if it is installed and does without otherwise.

## Contributing

See [CONTRIBUTING.md](https://github.com/agenteca/.github/blob/main/CONTRIBUTING.md). For a security vulnerability, see [SECURITY.md](https://github.com/agenteca/.github/blob/main/SECURITY.md).
