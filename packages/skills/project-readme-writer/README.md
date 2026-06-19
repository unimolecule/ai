# `@unimolecule/ai-project-readme-writer-skill`

<p><strong>English</strong> | <a href="./README.zh-CN.md">Chinese</a></p>

This private workspace package contains the `project-readme-writer` Codex skill. Use it to inspect a repository or workspace package, detect its project shape, and write a README that fits the reader's real task instead of applying a fixed generic outline.

It supports:

- README writing and structure reviews for repositories, packages, apps, CLIs, examples, and monorepos.
- Project-shape detection from manifests, workspace configuration, scripts, entrypoints, and existing docs.
- Template routing for root READMEs, package READMEs, app READMEs, and localized README variants.

This package is documentation and prompt configuration only. It does not expose a TypeScript API, publish a CLI, or own repository-level tooling outside this skill directory.

## Architecture

`SKILL.md` is the entrypoint that tells Codex when to use the skill and which references to read. `references/project-detection.md` provides the required discovery pass, while the other reference files provide scoped README structures. `agents/openai.yaml` stores the OpenAI-facing display metadata and default prompt.

## Requirements

- Node.js `26.2.0`, as declared in the workspace configuration.
- pnpm `>=11.0.0`, as declared by the root package metadata.
- Python 3 for the Codex skill validator.

## Getting Started

Install workspace dependencies from the repository root:

```bash
pnpm install
```

Validate this skill package:

```bash
python3 /Users/i7eo/.codex/skills/.system/skill-creator/scripts/quick_validate.py packages/skills/project-readme-writer
```

Check Markdown and package formatting from the repository root:

```bash
pnpm exec prettier --check packages/skills/project-readme-writer
```

## Package Contents

| Path                                                                               | Purpose                                                                                |
| ---------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [`SKILL.md`](./SKILL.md)                                                           | Skill frontmatter, routing rules, workflow, writing rules, and common mistakes.        |
| [`agents/openai.yaml`](./agents/openai.yaml)                                       | Display name, short description, and default prompt for OpenAI tooling.                |
| [`references/project-detection.md`](./references/project-detection.md)             | Required discovery rules for classifying project shape before writing.                 |
| [`references/root-readme-template.md`](./references/root-readme-template.md)       | Root README structures for single-project repositories and monorepos.                  |
| [`references/package-readme-template.md`](./references/package-readme-template.md) | README structure for libraries, adapters, SDKs, tools, and internal packages.          |
| [`references/app-readme-template.md`](./references/app-readme-template.md)         | README structure for runnable apps, services, CLIs, docs sites, workers, and examples. |
| [`references/language-readmes.md`](./references/language-readmes.md)               | Rules for English source READMEs and localized README variants.                        |

## Usage

Invoke the skill when README structure is the main task:

```text
Use $project-readme-writer to inspect this repository and write a README that fits its project shape.
```

When updating the skill, keep the workflow in `SKILL.md` short and move longer routing rules or examples into `references/`. Add new reference files only when they describe reusable README decisions that would make the entrypoint too large.

## Maintenance

Before changing README behavior:

1. Update `SKILL.md` when the trigger conditions, workflow, or core writing rules change.
2. Update the relevant file in `references/` when a template or discovery rule changes.
3. Keep `agents/openai.yaml` aligned when the display name, short description, or default prompt changes.
4. Run the skill validator and Prettier checks shown above.

## Runtime Notes

This is a private package in the `@unimolecule/ai` pnpm workspace. The `private: true` package metadata means it is maintained as a local skill package, not as a published npm package.
