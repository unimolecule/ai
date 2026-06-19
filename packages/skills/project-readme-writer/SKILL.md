---
name: project-readme-writer
description: Use when writing or updating project README files for repositories, apps, packages, libraries, CLIs, examples, monorepos, workspace packages, or README structure reviews. Use for repo inspection, README information architecture, project positioning, command documentation, architecture summaries, and contributor-facing setup guidance.
---

# Project README Writer

Write README files that fit the actual project shape. The core job is to inspect the repository, identify the reader's primary task, then choose the right README structure instead of forcing every project into the same outline.

## Quick Routing

| User intent                                                                                       | Action                                                    |
| ------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Write or update this repo's README                                                                | Use this skill                                            |
| Review README structure or missing sections                                                       | Use this skill                                            |
| Translate README files, add language selectors, or maintain localized README variants             | Prefer a dedicated README i18n skill when available       |
| Write tutorials, how-to guides, reference docs, or explanations beyond the README                 | Prefer a Diataxis documentation skill when available      |
| Advise on open source governance, contributor onboarding, community health, or maintainer process | Prefer an open source guide/coaching skill when available |

Use this skill when README structure is the main task, even if the README includes small localized links or contribution notes.

## Reference Routing

Read only the relevant references:

- Always read `references/project-detection.md` before choosing scope or template.
- Read `references/language-readmes.md` only when localized README files are requested or already present.
- Read `references/root-readme-template.md` for repository root README work.
- Read `references/package-readme-template.md` for library, SDK, adapter, tool, codegen, or package work.
- Read `references/app-readme-template.md` for apps, services, CLIs, workers, docs sites, runnable examples, or deployable entrypoints.

If a project fits multiple templates, choose by the reader's primary job. For example, a deployable app with an internal helper package should usually use the app template unless the user asks for package documentation too.

## Workflow

1. Detect the project shape.
   - Read manifests, existing README files, scripts, entrypoints, framework/deployment config, and workspace files when present.
   - Classify the repo as a single app, package/library, CLI/tool, docs site, runnable example, infrastructure repo, or monorepo.

2. Build a project map.
   - Capture name, runtime/platform, public/private status, important commands, requirements, entrypoints, and one-sentence purpose.
   - For monorepos, map each workspace's relative path, type, scripts, dependencies, and relationship to other workspaces.

3. Write the README at the right level.
   - For a single project, make the root README the primary operational guide.
   - For a monorepo, keep the root README navigational and architectural, then place deep setup details in workspace READMEs.
   - Preserve accurate existing warnings, migration notes, badges, compatibility notes, commands, and troubleshooting details.

4. Validate the output.
   - Ensure package names, commands, links, paths, and public/private status match repo files.
   - Ensure workspace links resolve.
   - Ensure examples are runnable or clearly marked as illustrative.

## Writing Rules

- Organize by reader intent first, filesystem second.
- Do not force monorepo sections into single-project READMEs.
- Do not turn the README into a full documentation site; link out when details grow.
- Do not invent scripts, package publication status, deployment targets, credentials, or badges.
- Put package setup details in package READMEs and app operation details in app READMEs.
- Explain how packages, apps, or modules compose, not just what directories exist.
- Keep tables scannable and descriptions to one sentence.
- Prefer exact package scripts from manifests over guessed commands.

## Common Mistakes

- Treating folder names as truth without reading manifests and entrypoints.
- Replacing a useful existing README instead of preserving correct content and improving structure.
- Writing monorepo navigation for a single app or library.
- Duplicating deep API reference in the README instead of linking to docs.
- Translating or rewriting code blocks, badge URLs, env var names, package names, or relative links accidentally.
