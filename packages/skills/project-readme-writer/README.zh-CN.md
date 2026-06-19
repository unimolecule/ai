# `@unimolecule/ai-project-readme-writer-skill`

<p><a href="./README.md">English</a> | <strong>Chinese</strong></p>

这个私有 workspace package 包含 `project-readme-writer` Codex skill。它用于检查仓库或 workspace package，识别项目形态，并编写符合真实读者任务的 README，而不是套用固定的通用大纲。

它支持：

- 为仓库、package、app、CLI、example 和 monorepo 编写 README 或审查 README 结构。
- 根据 manifest、workspace 配置、scripts、入口文件和现有文档识别项目形态。
- 为 root README、package README、app README 和本地化 README 选择合适模板。

这个 package 只包含文档和 prompt 配置。它不暴露 TypeScript API，不发布 CLI，也不负责 skill 目录之外的仓库级工具。

## Architecture

`SKILL.md` 是入口文件，说明 Codex 何时使用这个 skill，以及需要读取哪些 reference。`references/project-detection.md` 提供必需的发现流程，其他 reference 文件提供对应范围的 README 结构。`agents/openai.yaml` 保存 OpenAI 工具侧展示所需的名称、简短说明和默认 prompt。

## Requirements

- Node.js `26.2.0`，由 workspace 配置声明。
- pnpm `>=11.0.0`，由根 package metadata 声明。
- Python 3，用于运行 Codex skill validator。

## Getting Started

从仓库根目录安装 workspace 依赖：

```bash
pnpm install
```

验证这个 skill package：

```bash
python3 /Users/i7eo/.codex/skills/.system/skill-creator/scripts/quick_validate.py packages/skills/project-readme-writer
```

从仓库根目录检查 Markdown 和 package 格式：

```bash
pnpm exec prettier --check packages/skills/project-readme-writer
```

## Package Contents

| Path                                                                               | Purpose                                                                        |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [`SKILL.md`](./SKILL.md)                                                           | Skill frontmatter、routing rules、workflow、writing rules 和 common mistakes。 |
| [`agents/openai.yaml`](./agents/openai.yaml)                                       | OpenAI tooling 使用的展示名称、简短说明和默认 prompt。                         |
| [`references/project-detection.md`](./references/project-detection.md)             | 写作前用于识别项目形态的必读发现规则。                                         |
| [`references/root-readme-template.md`](./references/root-readme-template.md)       | 单项目仓库和 monorepo 的 root README 结构。                                    |
| [`references/package-readme-template.md`](./references/package-readme-template.md) | Library、adapter、SDK、tool 和内部 package 的 README 结构。                    |
| [`references/app-readme-template.md`](./references/app-readme-template.md)         | 可运行 app、service、CLI、docs site、worker 和 example 的 README 结构。        |
| [`references/language-readmes.md`](./references/language-readmes.md)               | English 源 README 与本地化 README 变体的规则。                                 |

## Usage

当 README 结构是主要任务时调用这个 skill：

```text
Use $project-readme-writer to inspect this repository and write a README that fits its project shape.
```

维护这个 skill 时，让 `SKILL.md` 保持简洁，并把较长的 routing rules 或 examples 放进 `references/`。只有当新内容描述的是可复用 README 决策，并且会让入口文件过长时，才新增 reference 文件。

## Maintenance

修改 README 行为前：

1. 如果触发条件、workflow 或核心 writing rules 改变，更新 `SKILL.md`。
2. 如果 template 或 discovery rule 改变，更新 `references/` 中对应文件。
3. 如果展示名称、简短说明或默认 prompt 改变，同步更新 `agents/openai.yaml`。
4. 运行上方的 skill validator 和 Prettier 检查。

## Runtime Notes

这是 `@unimolecule/ai` pnpm workspace 中的私有 package。`private: true` package metadata 表示它作为本地 skill package 维护，而不是发布到 npm。
