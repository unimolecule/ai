# Unimolecule AI

[![skills.sh](https://skills.sh/b/unimolecule-org/ai)](https://www.skills.sh/unimolecule/ai)

This repository contains Codex skills maintained by Unimolecule. The current focus is project documentation skills under `packages/skills/**`.

## Skills

| Skill                                                                     | Description                                                                                                                     |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| [`project-readme-writer`](./packages/skills/project-readme-writer#readme) | Inspects a repository, identifies its project shape, and writes README files for apps, packages, CLIs, examples, and monorepos. |

## Install

Install the current skill with the skills CLI:

```bash
npx skills add https://github.com/unimolecule-org/ai --skill project-readme-writer
```

## Development

```bash
pnpm install
pnpm exec prettier --check .
python3 /Users/i7eo/.codex/skills/.system/skill-creator/scripts/quick_validate.py packages/skills/project-readme-writer
```

Skill source lives in `packages/skills/<skill-name>/`. Keep `SKILL.md` concise and put larger routing rules, templates, and examples in `references/`.

## License

MIT
