# Bukit Agent Skills

[English](./README.md) | [Bahasa Melayu](./README.ms.md)

`BukitSkills` 是一个面向 AI Agent 的 Bukit 专项技能仓库。仓库核心内容是根目录 `skills/` 下的一组 `SKILL.md` 文档，用来帮助 Agent 在使用 Bukit 时快速定位正确的知识边界，而不是提供 Bukit 本体源码或可直接运行的站点项目。

如果你在 Trae、Claude Code、Copilot CLI、Codex CLI、Gemini CLI 等支持 skill 的环境中使用 Bukit，可以把这里理解成 Agent 侧的“知识导航层”：

- 明确提到 “using bukit / 使用 bukit” 时，先进入 `using-bukit`
- 需要执行命令时，统一参考 `bukit-cli-reference`
- 需要修改 `site.yaml`、主题、模板、Notion、路由、多语言或插件时，再进入对应子 skill

## 项目定位

- 这是技能文档仓库，不是运行时代码仓库
- 仓库本身没有 `package.json`、`site.yaml`、Docker 或 CI 配置
- 这里沉淀的是 Bukit 的任务拆分方式、配置知识和操作指引
- 推荐把它作为 Agent 处理 Bukit 任务时的入口、索引和速查手册

## 仓库结构

```text
BukitSkills/
  README.md
  README.zh-CN.md
  README.ms.md
  skills/
    using-bukit/            # 统一入口与任务路由
    bukit-cli-reference/    # CLI 操作单一事实来源
    bukit-config/           # site.yaml 配置模型
    bukit-theme/            # 主题目录、资源与参数
    bukit-templating/       # Scriban 模板开发
    bukit-notion/           # Notion 内容源接入
    bukit-routing/          # URL 路由与 permalink
    bukit-i18n/             # 多语言站点
    bukit-plugins-debug/    # 插件、增量构建与排障
```

## Skills 一览

| Skill | 主要职责 | 适用场景 |
|---|---|---|
| `using-bukit` | Bukit 任务总入口，识别任务并路由到子 skill | 用户明确说“using bukit / 使用 bukit”，或任务已确定采用 Bukit |
| `bukit-cli-reference` | CLI 检测、安装、命令速查、输出与退出码解释 | 需要执行 `bukit build`、`init`、`preview`、`doctor`、`theme`、`webhook` 等命令 |
| `bukit-config` | `site.yaml` 的配置模型、场景模板与字段说明 | 创建或修改站点配置、解释字段含义、修复配置错误 |
| `bukit-theme` | 主题目录、静态资源组织与主题参数 | 从零搭主题、迁移主题、处理 CSS 或静态资源问题 |
| `bukit-templating` | Scriban 语法、layout 继承与模板模式 | 编写页面模板、列表页、分页组件、排查模板报错 |
| `bukit-notion` | Notion API 接入、字段映射、块渲染、图片本地化 | 用 Notion 做 CMS、排查拉取失败或映射错误 |
| `bukit-routing` | permalink、集合路由、URL 编码与输出路径 | 自定义 URL 结构、处理路由冲突、配置列表页 |
| `bukit-i18n` | 语言检测、分语言构建与产物合并 | 搭建多语言站点、排查语言切换与输出合并问题 |
| `bukit-plugins-debug` | 插件生命周期、增量构建、性能诊断与排障 | 插件不生效、构建结果异常、构建性能退化 |

## 如何使用本仓库

推荐按照下面的顺序加载技能：

1. 当任务已经明确是 Bukit 任务时，先看 `using-bukit`
2. 凡是要执行命令，都以 `bukit-cli-reference` 为准
3. 涉及配置背景知识时，优先补充 `bukit-config`
4. 主题相关任务先看 `bukit-theme`，模板开发再看 `bukit-templating`
5. 进阶场景按需进入 `bukit-notion`、`bukit-routing`、`bukit-i18n`、`bukit-plugins-debug`

一条常见工作流可以概括为：

```text
using-bukit
  -> bukit-cli-reference
  -> bukit-config
  -> bukit-theme / bukit-notion / bukit-routing / bukit-i18n / bukit-plugins-debug
  -> bukit-templating
```

## Bukit 最小体验流程

本仓库本身不是 Bukit 站点，不能在仓库根目录直接执行 `bukit build` 或 `bukit preview`。如果你想体验 Bukit 的最小工作流，请在一个真实站点目录中执行：

```bash
bukit version
bukit init ./my-site --provider markdown
cd my-site
bukit build
bukit preview
```

补充说明：

- `bukit build` 和 `bukit preview` 需要在包含 `site.yaml` 的站点根目录执行
- 默认输出目录通常是 `dist`
- 使用 Notion 作为内容源时，通常还需要配置 `NOTION_TOKEN`
- Windows 下如果你直接调用可执行文件，常见形式是 `.\bukit.exe version` 或 `& .\bukit.exe version`

## 常见任务与推荐阅读路径

### 从零创建站点

1. `using-bukit`
2. `bukit-cli-reference`
3. `bukit-config`
4. `bukit-theme`
5. `bukit-templating`

### 接入 Notion 作为内容源

1. `using-bukit`
2. `bukit-notion`
3. `bukit-config`
4. `bukit-cli-reference`

### 调整 URL、分类页或列表页

1. `using-bukit`
2. `bukit-routing`
3. `bukit-config`
4. `bukit-templating`

### 排查构建异常或插件问题

1. `using-bukit`
2. `bukit-plugins-debug`
3. `bukit-config`
4. `bukit-cli-reference`

## 维护约定

为避免 skill 信息和真实实现脱节，维护时建议遵循以下规则：

- 每个 skill 固定放在 `skills/<skill-name>/SKILL.md`
- `description` 只写触发条件，不写泛化介绍
- CLI 指令与执行注意事项统一收敛到 `bukit-cli-reference`
- 主题目录、配置字段、CLI 参数应与 Bukit 实际行为保持一致
- 新增 Bukit 能力时，优先判断是扩充现有 skill 还是新增独立 skill

## 文档说明

- 默认英文入口：[`README.md`](./README.md)
- 中文说明：[`README.zh-CN.md`](./README.zh-CN.md)
- 马来文说明：[`README.ms.md`](./README.ms.md)
- 所有技能文档位于 [`skills/`](./skills)
