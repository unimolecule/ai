# Project Detection

Detect the repository shape before choosing a README template. Do not assume JavaScript, pnpm, or monorepo layout from folder names alone.

## Primary Files to Read

Read the smallest useful set first:

- Existing `README*`, `CONTRIBUTING*`, `SECURITY*`, `docs/`, and examples.
- Root metadata: `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `composer.json`, `.csproj`, `Gemfile`, `Makefile`, `justfile`, `Dockerfile`, and CI files.
- Tooling config: workspace files, task runners, framework configs, deployment configs, and test configs.
- Source entrypoints such as `src/`, `app/`, `apps/`, `packages/`, `cmd/`, `crates/`, `examples/`, `docs/`, or `tools/`.

## Project Shape Signals

| Shape               | Strong signals                                           | README emphasis                                     |
| ------------------- | -------------------------------------------------------- | --------------------------------------------------- |
| Single app/service  | One runtime entrypoint, deploy scripts, env config       | Run locally, environment, architecture, deployment  |
| Package/library     | Exports, package metadata, public API, no deploy target  | Install, usage, API, runtime boundaries             |
| CLI/tool            | Bin entrypoint, commands, flags, examples                | Install, commands, examples, configuration          |
| Documentation site  | Content directories, static-site config, publish scripts | Authoring, preview, build, publishing               |
| Runnable example    | Demo app, sample config, limited scope                   | What it demonstrates, setup, expected result        |
| Monorepo            | Explicit workspace/project graph files                   | Root navigation plus workspace-local README details |
| Infrastructure repo | Terraform/Pulumi/Kubernetes/Docker-focused layout        | Requirements, plans/apply/deploy, state, safety     |

If the shape is mixed, pick the reader's primary job. For example, a deployable app with a small internal package should use the app structure unless the user asks for package documentation too.

## Workspace and Monorepo Detection

Do not assume pnpm. Detect the workspace system from root files and use the first matching source of truth.

| System           | Primary files to read                           | Workspace source                                                  |
| ---------------- | ----------------------------------------------- | ----------------------------------------------------------------- |
| pnpm workspaces  | `pnpm-workspace.yaml`, root `package.json`      | `packages` globs in `pnpm-workspace.yaml`                         |
| npm workspaces   | root `package.json`, `package-lock.json`        | `workspaces` field                                                |
| Yarn workspaces  | root `package.json`, `yarn.lock`, `.yarnrc.yml` | `workspaces` field                                                |
| Bun workspaces   | root `package.json`, `bun.lockb` / `bun.lock`   | `workspaces` field                                                |
| Lerna            | `lerna.json`, root `package.json`               | `packages` in `lerna.json`, falling back to `workspaces`          |
| Nx               | `nx.json`, `project.json`, root `package.json`  | Nx project graph/config plus package manifests                    |
| Turborepo        | `turbo.json`, root `package.json`               | Package manager workspaces; `turbo.json` supplies task graph only |
| Rush             | `rush.json`                                     | `projects[*].projectFolder`                                       |
| Lage             | `lage.config.*`, root `package.json`            | Package manager workspaces                                        |
| Moon             | `.moon/workspace.yml`, `.moon/tasks.yml`        | Moon workspace projects                                           |
| Bazel-style repo | `MODULE.bazel`, `WORKSPACE`, `BUILD*`           | Infer from project files and docs                                 |

## Discovery Rules

- Prefer explicit project and workspace configuration over folder guesses.
- Treat manifests, scripts, package exports, bin entries, framework configs, deployment configs, and source entrypoints as evidence. Folder names are only hints.
- If multiple tools exist, treat package-manager workspace membership as the workspace list and task-runner files as build orchestration.
- Use exact commands from manifests, Makefiles, justfiles, CI, or existing docs. Do not invent build, test, deploy, or publish commands.
- Infer publish/deploy status only from metadata or config such as `private`, package registry fields, Docker/deployment files, CI release jobs, or existing docs.
- Read each workspace `package.json` when present, but support non-JS workspaces by reading project metadata and README files.
- Exclude `node_modules`, `dist`, build output, generated folders, vendored code, and hidden cache directories.
- If project shape or workspace membership is ambiguous, state the assumption before writing broad README changes.
- Do not create workspace tables for single-project repositories unless they clarify real modules or components.

## Project Map Fields

Capture these fields for a single project:

- Name or folder label
- Project shape
- Public/private status
- Runtime, framework, or platform
- Entrypoints
- Important scripts or commands
- Requirements: package manager, runtime version, env vars, services, credentials
- One-sentence purpose
- Known README language variants
- Related packages, services, or deployment targets

For monorepos, capture the same fields for the root plus each workspace, including relative path and relationship to other workspaces.
