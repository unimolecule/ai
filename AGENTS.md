# Repository Guidelines

## Project Structure & Module Organization

This repository is a private pnpm workspace dedicated to Codex skills. Treat `packages/skills/**` as the only long-term product area, even though `pnpm-workspace.yaml` also allows `apps/**`.

- Root configuration lives at the top level: `package.json`, `tsconfig.json`, `tsconfig.node.json`, `prettier.config.ts`, `lint-staged.config.ts`, and `commitlint.config.ts`.
- Skills live under `packages/skills/<skill-name>/`; the current skill is `packages/skills/project-readme-writer/`.
- Skill documentation starts in `SKILL.md`; reusable prompt or agent config belongs in `agents/`; supporting templates and reference material belong in `references/`.
- Add `scripts/` only for reusable executable helpers and `assets/` only for files the skill needs to copy or emit. Do not add app workspaces unless the repository purpose changes.

## Build, Test, and Development Commands

- `pnpm install` installs dependencies and registers `simple-git-hooks`.
- `pnpm lint` runs workspace `lint` scripts when a skill package defines one.
- `pnpm exec prettier --check .` checks repository formatting.
- `pnpm clean` runs all clean tasks, including workspace cleanup and cache cleanup.
- `pnpm clean:workspace` runs `clean` in every workspace package.
- `pnpm clean:cache` removes `pnpm-lock.yaml` and `node_modules`; use this only when resetting local dependency state.
- `pnpm commit` opens the Commitizen/CZG prompt for conventional commits.
- `pnpm upgrade:pkgs` interactively updates workspace dependencies.
- `python3 /Users/i7eo/.codex/skills/.system/skill-creator/scripts/quick_validate.py packages/skills/<skill-name>` validates skill frontmatter and naming.

## Coding Style & Naming Conventions

Use TypeScript and ESM conventions for configuration and tooling files. Prettier is the formatting source of truth: semicolons, double quotes, trailing commas, and LF endings. Keep Markdown headings descriptive and sentence-style.

Name skills in lowercase hyphen-case and keep the folder name identical to the `SKILL.md` frontmatter `name`. Use concise descriptions that start with `Use when...` and describe trigger conditions. Keep `SKILL.md` lean; move longer templates, routing rules, and examples into `references/`.

## Testing Guidelines

No test runner or coverage threshold is configured yet. When adding executable code, add a package-local test script and document it in that skill's README or guide. Prefer colocated tests or a package-level `tests/` directory. Use names such as `<feature>.test.ts` when a runner is introduced.

Before opening a PR, run `pnpm exec prettier --check .` and `quick_validate.py` for each changed skill. If you add a test command, run it directly, for example `pnpm -F <package-name> test`.

## Commit & Pull Request Guidelines

Commits are validated with `@commitlint/config-conventional`. Use conventional commit types, lowercase scopes, and no trailing period in the subject. Valid scopes include workspace package names plus `.github`, `.vscode`, `docs`, `scripts`, and `repository-config`.

Example: `feat(@unimolecule/ai): add skill package`

Pull requests should include a concise summary, commands run, linked issues when applicable, and screenshots only for visual changes. Call out new skills, dependency changes, and any missing tests.
