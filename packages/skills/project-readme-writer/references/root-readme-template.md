# Root README Template

Use this outline for the repository root. Choose the single-project or monorepo variant after reading `project-detection.md`.

## Universal Opening

```markdown
# <Repo / project name>

Badges, when useful.

Language links, when localized READMEs exist.

Important warning, migration note, compatibility note, or project status note.

One short paragraph explaining what this repository is, who it serves, and what outcome it enables.
```

Keep the opening concrete. Do not say "collection of workspaces" unless the repo is actually a monorepo.

## Single-Project Root README

Use this for one app, service, CLI, library, docs site, infrastructure repo, or runnable example.

````markdown
## Getting started

Show the shortest path from checkout to useful result.

```bash
<package-manager> install
<package-manager> <primary-command>
```
````

## Requirements

List runtime, package manager, accounts, services, credentials, databases, or generated files.

## Commands

| Command     | Description   |
| ----------- | ------------- |
| `<command>` | What it does. |

## Architecture

Summarize the main runtime, entrypoints, modules, integrations, and deployment boundary in one short paragraph or compact diagram.

## Configuration

Document env files, public/private env boundaries, config files, or required secrets when relevant.

## Testing

Explain test commands and what they cover when tests exist.

## Deployment / Publishing

Include only when the project is deployable or publishable.

## Troubleshooting

List likely setup, runtime, or deployment failures only when the repo already reveals them.

````

## Monorepo Root README

Use this only when explicit workspace or project graph configuration exists.

```markdown
## Getting started

Show root install and the primary repo-level command.

## Workspaces

Group by reader intent, not folder names.

| Workspace | Type | Description |
| --- | --- | --- |
| [`<name>`](./relative/path#readme) | app / package / tool | One-sentence purpose. |

## Architecture

Summarize dependency topology:

`primitives` -> `core libraries` -> `runtime adapters` -> `apps / deployment targets`

## Developing in this repo

List root build/test/lint commands and workspace-scoped examples.

## Testing a local package in an app

Show a `file:` or workspace-aware local install flow only when useful.
````

Common workspace groups include apps, API clients, adapters, tooling, examples, documentation, storage, infrastructure, and deployment targets.

## Deep Links

Add these sections only when relevant and backed by repo files:

- `Documentation`: guides, API reference, examples, docs site.
- `Contributing`: contribution guide, local development expectations, review requirements.
- `Community`: discussions, support channels, issue tracker.
- `Security`: responsible disclosure or security policy. Do not tell users to open public issues for vulnerabilities.

## Link Rules

- Link workspace names with relative links: ``[`@scope/pkg`](./packages/group/pkg#readme)`` or ``[`app-name`](./apps/name#readme)``.
- Prefer links to workspace folders with `#readme`, so GitHub opens that README naturally.
- Do not link to npm as the primary workspace link; npm badges can link to npm.
- If a workspace lacks README, either create one or link to the folder only if it contains useful source docs.
- Keep root workspace descriptions short enough to scan.
