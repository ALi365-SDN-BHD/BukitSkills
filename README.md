# Bukit Agent Skills

[简体中文](./README.zh-CN.md) | [Bahasa Melayu](./README.ms.md)

`BukitSkills` is a Bukit-focused skill repository for AI agents. The core assets live in the top-level `skills/` directory as focused `SKILL.md` files. This repository is not the Bukit runtime source and is not a ready-to-run site project. Instead, it helps an agent pick the right knowledge boundary when working with Bukit.

If you use Bukit from Trae, Claude Code, Copilot CLI, Codex CLI, Gemini CLI, or another skill-aware environment, treat this repository as the agent-side navigation layer:

- Start with `using-bukit` when the task explicitly uses Bukit
- Use `bukit-cli-reference` as the single source of truth for command execution
- Load the matching sub-skill for config, theme, templating, Notion, routing, i18n, or plugin/debug work

## Project Scope

- This is a skill documentation repository, not a runtime code repository
- The repository itself does not include `package.json`, `site.yaml`, Docker, or CI setup
- It captures Bukit task decomposition, config knowledge, and execution guidance
- It works best as the entry point, index, and quick reference for agents handling Bukit tasks

## Repository Layout

```text
BukitSkills/
  README.md
  README.zh-CN.md
  README.ms.md
  skills/
    using-bukit/            # Unified entry point and routing
    bukit-cli-reference/    # Single source of truth for CLI operations
    bukit-config/           # site.yaml configuration model
    bukit-theme/            # Theme directories, assets, and params
    bukit-templating/       # Scriban template development
    bukit-notion/           # Notion content source integration
    bukit-routing/          # URL routing and permalinks
    bukit-i18n/             # Multilingual sites
    bukit-plugins-debug/    # Plugins, incremental build, diagnostics
```

## Skill Overview

| Skill | Responsibility | Typical use case |
|---|---|---|
| `using-bukit` | Bukit gateway skill that identifies work and routes to sub-skills | The user explicitly says "using bukit" or the task is clearly Bukit-specific |
| `bukit-cli-reference` | CLI detection, installation guidance, command reference, output, and exit-code interpretation | Running `bukit build`, `init`, `preview`, `doctor`, `theme`, `webhook`, and related commands |
| `bukit-config` | `site.yaml` structure, scenario templates, and field explanations | Creating or editing site config, explaining fields, fixing validation errors |
| `bukit-theme` | Theme directory structure, static asset organization, and theme parameters | Creating or migrating themes, fixing CSS or static asset issues |
| `bukit-templating` | Scriban syntax, layout inheritance, and template patterns | Writing page templates, list pages, pagination, or fixing template rendering issues |
| `bukit-notion` | Notion integration, property mapping, block rendering, and image localization | Using Notion as a CMS or troubleshooting Notion fetch and mapping problems |
| `bukit-routing` | Permalinks, collection routes, URL encoding, and output path behavior | Customizing URLs, fixing 404s, handling route conflicts, configuring list pages |
| `bukit-i18n` | Language detection, per-language builds, and merged outputs | Building multilingual sites and debugging language switching or merged output behavior |
| `bukit-plugins-debug` | Plugin lifecycle, incremental build behavior, performance diagnostics, and troubleshooting | Plugins do not run, output looks wrong, or build performance regresses |

## How To Use This Repository

Recommended loading order:

1. Start from `using-bukit` once the task is confirmed to be a Bukit task
2. Use `bukit-cli-reference` for every command-related step
3. Load `bukit-config` whenever the task depends on config background knowledge
4. Read `bukit-theme` before `bukit-templating` when template work depends on theme structure
5. Move into `bukit-notion`, `bukit-routing`, `bukit-i18n`, or `bukit-plugins-debug` as needed

A common workflow looks like this:

```text
using-bukit
  -> bukit-cli-reference
  -> bukit-config
  -> bukit-theme / bukit-notion / bukit-routing / bukit-i18n / bukit-plugins-debug
  -> bukit-templating
```

## Minimal Bukit Flow

This repository is not itself a Bukit site. Do not run `bukit build` or `bukit preview` from this repo root. To try a minimal Bukit flow, run the commands inside a real Bukit site directory:

```bash
bukit version
bukit init ./my-site --provider markdown
cd my-site
bukit build
bukit preview
```

Notes:

- `bukit build` and `bukit preview` must run in a site root that contains `site.yaml`
- The default output directory is typically `dist`
- Notion-based sites usually require `NOTION_TOKEN`
- On Windows, direct executable usage often looks like `.\bukit.exe version` or `& .\bukit.exe version`

## Suggested Reading Paths

### Create a new site

1. `using-bukit`
2. `bukit-cli-reference`
3. `bukit-config`
4. `bukit-theme`
5. `bukit-templating`

### Configure Notion as content source

1. `using-bukit`
2. `bukit-notion`
3. `bukit-config`
4. `bukit-cli-reference`

### Customize routing and list pages

1. `using-bukit`
2. `bukit-routing`
3. `bukit-config`
4. `bukit-templating`

### Debug build or plugin issues

1. `using-bukit`
2. `bukit-plugins-debug`
3. `bukit-config`
4. `bukit-cli-reference`

## Maintenance Notes

- Keep each skill at `skills/<skill-name>/SKILL.md`
- Use `description` only for trigger conditions, not generic summaries
- Centralize CLI instructions and execution notes in `bukit-cli-reference`
- Keep theme paths, config fields, and CLI parameters aligned with actual Bukit behavior
- When Bukit gains new capabilities, decide whether to extend an existing skill or add a new one with a clear boundary

## Docs

- English: [`README.md`](./README.md)
- Chinese: [`README.zh-CN.md`](./README.zh-CN.md)
- Malay: [`README.ms.md`](./README.ms.md)
- All skill documents live in [`skills/`](./skills)
