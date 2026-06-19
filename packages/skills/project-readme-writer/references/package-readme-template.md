# Package README Template

Use this outline for library-style workspaces. Common folders include `packages/*`, `libs/*`, `modules/*`, `crates/*`, `sdk/*`, `clients/*`, `adapters/*`, `plugins/*`, `tools/*`, and library examples. Folder names are signals, not rules; choose this template for publishable libraries, internal shared packages, SDKs, adapters, storage packages, clients, tools, and codegen packages.

```markdown
# `<package-name>`

Badges, when useful.

Language links, when localized READMEs exist.

Important warning, breaking change, compatibility note, or version note.

One paragraph explaining what this package does, who should use it, and the primary outcome it enables.

It supports:

- Capability 1
- Capability 2
- Capability 3

Boundary note explaining runtime/framework independence and what the package does not do.

## Architecture

Summarize this package's role in the dependency graph in one short paragraph or compact diagram.

Example:

`schema primitives` -> `validation helpers` -> `runtime adapters`

Use professional terms such as primitives, core, adapter, driver, provider, transport, boundary, integration, and runtime. Keep this section concise; link to deeper docs instead of writing a full design essay.

## Requirements

List required runtime, credentials, peer services, package manager, framework version, or generated files.

## Getting started

Install/import command and shortest setup path.

## Configuration

Document required config fields with a table when the package exposes configuration.

## Usage

Show common tasks in increasing complexity.

## API

Document important exports, methods, response shapes, or interfaces.

## Guides

Link to task-oriented docs when the package has multi-step workflows.

## Reference

Link to detailed API/config/reference docs when the README would become too large.

## Runtime notes

Call out supported runtimes, browser/Node/Worker boundaries, security behavior, and performance assumptions.

## Gotchas / Troubleshooting

Only include issues users are likely to hit.

## Migrating

Add only when there are versioned breaking changes or migration paths.
```

## Package README Logic

1. Identity and trust: name, badges, language links.
2. Risk first: warnings and breaking changes before overview.
3. Positioning: what it is, who uses it, what outcome it enables.
4. Capabilities: scannable bullets that match why users arrived.
5. Boundaries: what the package does not own.
6. Architecture: concise dependency role and integration boundary.
7. Requirements: what readers need before installation or usage works.
8. Getting started: shortest working path.
9. Usage/API: common workflows first, detailed facts second.
10. Guides/reference: route deeper content out of the README.
11. Runtime notes/gotchas/migration: keep operational knowledge discoverable without blocking new users.

## Workspace Type Guidance

For low-level API/client packages:

- Explain required credentials or tokens.
- Show client initialization.
- Document request methods, options, retries, custom fetch, response shape, and errors.
- Include typed usage if TypeScript is central.

For core libraries:

- Explain framework/runtime independence.
- Document initialization.
- Explain major capabilities such as auth, sessions, webhooks, billing, clients, or runtime adapters.
- Link to deeper reference docs instead of bloating README.

For framework adapters:

- Explain which core package is wrapped.
- Show required routes, middleware/hooks, server config, frontend provider, headers, and testing helpers.
- Call out framework version requirements and migration status.

For storage or infrastructure adapters:

- State the shared interface implemented.
- Show constructor options.
- Document schema/table/namespace requirements.
- Call out migrations, refresh-token support, local-development caveats, and production warnings.

For tooling/codegen packages:

- Explain what files are generated and why.
- Show minimal config.
- Document exported helpers from low-level to high-level convenience APIs.
- Include multi-project examples only when common.
