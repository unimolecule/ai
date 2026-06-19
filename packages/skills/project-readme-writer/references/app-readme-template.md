# App README Template

Use this outline for runnable or deployable workspaces. Common folders include `apps/*`, `services/*`, `web/*`, `sites/*`, `workers/*`, `functions/*`, `examples/*`, `docs/*`, and `cli/*`. Folder names are signals, not rules; choose this template for deployable services, frontend apps, documentation apps, runnable examples, workers, CLIs, and operational entrypoints.

```markdown
# `<app-name>`

Badges, when useful.

Language links, when localized READMEs exist.

Important warning, deployment note, environment note, or compatibility note.

One paragraph explaining what this app does, who runs it, and what user or system outcome it provides.

It includes:

- Runtime or mode 1
- Feature area 2
- Integration 3

Boundary note explaining what this app owns and which shared packages or external services it depends on.

## Architecture

Summarize the app topology in one short paragraph or compact diagram.

Example:

`routing` -> `application services` -> `infrastructure adapters` -> `external platforms`

Use professional terms such as entrypoint, runtime, route, boundary, adapter, provider, integration, deployment target, and infrastructure. Keep this section concise; link to deeper docs or ADRs for detailed design.

## Requirements

List runtime, package manager, accounts, services, tunnels, database, storage, credentials, and required generated files.

## Getting started

Show the shortest local setup path from install to running app.

## Environment

Document required env files, public/private env boundaries, and generated config behavior.

## Commands

List local development, build, test, lint, preview, deploy, and package-scoped commands.

## Runtime behavior

Explain modes, adapters, request flow, background jobs, routing, storage, or deployment targets.

## Deployment

Document production build/deploy flow, generated artifacts, and platform-specific steps.

## Troubleshooting

Only include issues users are likely to hit while running, configuring, deploying, or debugging the app.

## Related packages

Link to shared packages this app consumes when useful.
```

## App README Logic

1. Identity and trust: name, badges, language links.
2. Operational risk first: warnings about env, deployment, generated files, compatibility, or data.
3. Purpose: what app runs and who uses or operates it.
4. Capabilities: scannable runtime/features/integrations.
5. Boundaries: app ownership and dependencies.
6. Architecture: concise app topology and runtime boundaries.
7. Requirements: accounts, services, credentials, package manager, local tunnel, database/storage.
8. Getting started: fastest local run.
9. Environment and commands: make repeated operation easy.
10. Runtime behavior: explain how the app works after the user can run it.
11. Deployment and troubleshooting: operational finish line and known failure modes.

## Workspace Type Guidance

For application workspaces:

- Explain local development before architecture.
- Document env files and generated config before deployment.
- List commands as operational entrypoints, not API reference.
- Keep user-facing setup steps separate from internal implementation details.
- Link to package READMEs for reusable library details instead of duplicating them.

For documentation apps:

- Explain authoring, local preview, build, publish/deploy, and content source boundaries.
- Avoid documenting runtime internals that belong to the apps or packages being documented.

For runnable examples:

- Explain what the example demonstrates.
- Keep setup short and link to underlying package READMEs for API details.
- Include expected output or verification steps.
