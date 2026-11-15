# Contributing to Agenteca

Thank you for your interest. This document applies to every repository of the organisation.

## Before writing code

- For a bug: open an issue in the repository concerned, with what is needed to reproduce it.
- For a feature: open an issue first to discuss it.
- For a security vulnerability: **no public issue**, see [SECURITY.md](SECURITY.md).

Issues and pull requests can be written in English or French. English reaches the most people.

## Guiding principle: reuse standards

Agenteca only invents a format when no standard covers the need. Before proposing a new file or a new field, check OpenAPM, Agent Skills, AGENTS.md, MCP, SemVer, SPDX, OpenAPI and SARIF. If none fits, explain why in the pull request.

The formats of the tools change fast: rely on their current official documentation, cite it, and write "not confirmed" rather than guess.

## Where code goes

The integrations (IDE extensions, plugins, MCP server) are thin shells over `ahub --json`. Any installation, resolution or security logic goes into `agenteca-core` or `agenteca-cli`, never into an integration.

## The two contracts

| Contract | File | Rule |
|---|---|---|
| Output of `ahub --json` | `agenteca-cli/schemas/cli-output.v1.schema.json` | Adding a field: minor version. Removing a field or changing its meaning: major version. |
| Server API | `agenteca-server/openapi.json` | Generated from the code (`npm run openapi`); same rule. |

A pull request that touches a contract says so in its description and updates `CHANGELOG.md`.

## Texts in five languages

The CLI, the web site and the editor extensions speak English, French, Spanish, Chinese and Hindi. English is the source language.

- Write every text shown to people in English, in the code, through the translation function of the repository (`t('…')` in TypeScript, `vscode.l10n.t` in the VS Code extension, `Texts.t("key")` in the JetBrains plugin).
- Add its translation to every catalog of the repository (`src/locales/*.json`, `l10n/*.json`, `messages/*.properties`). If you do not speak a language, leave the English text there and say so in the pull request: a native speaker will correct it.
- The tests fail when a text has no translation, when a translation is no longer used, or when its placeholders (`{0}`, `{1}`…) differ.
- Never translate error codes, JSON fields, command names, or the content of the files `ahub` writes.

Documentation and code comments are written in English.

## Security: non-negotiable rules

- Nothing is executed when a package is installed.
- Nothing is written without having been shown.
- A file edited by hand is never overwritten or deleted without explicit agreement.
- An integration driven by a model cannot override the scan.
- A feature that is not implemented fails visibly; it never pretends to protect.

## Quality

- Every change of behaviour comes with a test.
- `npm run lint`, `npm run typecheck` and `npm test` pass (for the JetBrains plugin: `./gradlew check`).
- Small, atomic commits, with messages in the imperative: `feat: …`, `fix: …`, `docs: …`, `test: …`, `chore: …`.
- Each repository follows SemVer and keeps a `CHANGELOG.md`.

## Developing locally

The repositories are developed side by side, in one folder, linked through an npm workspace (a `package.json` at the root that lists the repositories in `workspaces`). Each repository declares its dependencies on the others with normal versions (`^0.1.0`).

## Contributor agreement

| Repositories | What is asked |
|---|---|
| Under Apache-2.0 | **DCO**: sign off each commit with `git commit -s`. See [DCO.md](DCO.md). |
| `agenteca-server`, `agenteca-web` (AGPL-3.0), `agenteca-ee` | **CLA**: see [CLA.en.md](CLA.en.md) (English translation) and [CLA.md](CLA.md) (French, binding). |

Why a CLA for the server and the web site: they are under the AGPL, and the proprietary premium module plugs into them. Only the rights holder can combine the two; they therefore need sufficient rights in each contribution.

## Code of conduct

Taking part in the project is subject to the [code of conduct](CODE_OF_CONDUCT.md).
