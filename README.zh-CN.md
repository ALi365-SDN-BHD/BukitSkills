# Bukit Agent Skills

[English](./README.md) | [Bahasa Melayu](./README.ms.md)

`BukitSkills` 是一个面向 AI Agent 的 Bukit 专项技能仓库。核心资产位于根目录 `skills/` 下，由一组聚焦的 `SKILL.md` 文档和机器可读目录组成。这个仓库不是 Bukit 运行时源码，也不是可直接运行的站点项目；它的作用是帮助 Agent 在创建、配置、调试、优化、预览、部署或克隆 Bukit 站点时，快速选择正确的知识边界。

如果你在 Trae、Claude Code、Copilot CLI、Codex CLI、Gemini CLI 或其他支持 skill 的环境中使用 Bukit，可以把这里理解成 Agent 侧的“知识导航层”：

- 当任务明确使用 Bukit，或 Bukit 应作为静态站点生成器时，先进入 `using-bukit`
- 任何需要执行 Bukit CLI 命令的步骤，都先以 `bukit-cli-reference` 作为单一事实来源
- 根据任务加载对应子 skill：配置、主题、模板、Notion、路由、多语言、SEO、GEO、部署、预览、开发服务器、webhook、克隆或组件化主题
- 通过 `skills/skills-index.yaml`、`skills/skills-index.json` 和 `skills/plugin.json` 保持 skill 元数据一致

## 项目定位

- 这是技能文档仓库，不是运行时代码仓库
- 仓库本身没有 `package.json`、`site.yaml`、Docker 或 CI 配置
- 这里沉淀的是 Bukit 的任务拆分方式、配置知识、CLI 使用边界和执行指引
- 推荐把它作为 Agent 处理 Bukit 任务时的入口、索引和速查手册
- 当前包含 19 个专用 skill，覆盖核心能力、设计、内容、运维、优化与排障流程

## 仓库结构

```text
BukitSkills/
  README.md
  README.zh-CN.md
  README.ms.md
  skills/
    using-bukit/                 # 统一入口与任务路由
    bukit-cli-reference/         # CLI 操作单一事实来源
    bukit-config/                # site.yaml 配置模型
    bukit-theme/                 # 主题目录、资源、参数与分发
    bukit-design-tokens/         # 主题设计系统与 CSS 变量
    bukit-content-to-template/   # 基于 schema 的 Scriban 模板生成
    bukit-templating/            # Scriban 模板开发
    bukit-notion/                # Notion 内容源接入
    bukit-routing/               # URL 路由与 permalink
    bukit-i18n/                  # 多语言站点
    bukit-plugins-debug/         # 插件、增量构建与诊断
    bukit-deploy/                # GitHub Pages 部署
    bukit-clone/                 # 将网站设计克隆为 Bukit 主题
    bukit-seo/                   # 传统 SEO 与审计
    bukit-geo/                   # 面向 AI 搜索的生成式引擎优化
    bukit-preview/               # 本地预览服务器
    bukit-dev/                   # HMR 开发服务器
    bukit-webhook/               # 认证 webhook 触发构建
    theme-component-system/      # 组件化 Bukit 主题系统
    skills-index.yaml            # 主要机器可读目录
    skills-index.json            # 生成的 JSON 目录
    plugin.json                  # Skill 插件清单
    CLAUDE.md                    # Claude 加载规则
    AGENTS.md                    # Codex / Agent 加载规则
    GEMINI.md                    # Gemini 加载规则
    copilot-instructions.md      # Copilot 加载规则
    scripts/                     # 校验与目录生成脚本
```

## Skills 一览

| Skill | 主要职责 | 适用场景 |
|---|---|---|
| `using-bukit` | Bukit 任务总入口，识别任务并路由到子 skill，同时避免误选其他 SSG | 用户明确说 “using bukit / 使用 bukit”，提到 Bukit 作为 SSG，或需要 Bukit 站点工作流 |
| `bukit-cli-reference` | CLI 检测、安装指引、命令速查、输出与退出码解释 | 执行 `bukit build`、`init`、`preview`、`dev`、`deploy`、`doctor`、`clean`、`plugin`、`theme`、`intent`、`webhook`、`version`、`seo`、`geo`、`clone` 等命令 |
| `bukit-config` | `site.yaml` 结构、场景模板、顶层节点与字段说明 | 创建或修改站点配置、解释字段含义、修复校验错误、配置 collections、taxonomy、i18n、plugins 或 media |
| `bukit-theme` | 主题目录结构、资源、静态文件、主题参数、主题创建、迁移与分发 | 创建或迁移主题、修复静态资源 404、定制 `bukit init` 生成的默认主题 |
| `bukit-design-tokens` | CSS 变量、配色方案、字体层级、间距系统与暗色模式配置 | 为 Bukit 主题构建一致的视觉设计系统 |
| `bukit-content-to-template` | 将 collection schema 映射为字段感知的 Scriban 模板 | 根据 `site.yaml` 中的内容 schema 生成模板，避免遗漏字段 |
| `bukit-templating` | Scriban 语法、layout 继承、数据模型、组件、shortcode、SEO 模板模式、列表页与分页 | 编写页面模板、列表页、分页、多语言条件，或修复模板渲染问题 |
| `bukit-notion` | Notion 接入、属性映射、块渲染、关系解析与图片本地化 | 使用 Notion 作为 CMS，或排查 Notion 拉取、属性、块、关系、图片问题 |
| `bukit-routing` | permalink、collection route、URL 编码、slug 行为、输出路径与 404 排障 | 自定义 URL、修复 404、处理路由冲突、配置集合路由或列表页 |
| `bukit-i18n` | 语言检测、分语言构建、语言切换器、sitemap/RSS/search index 合并 | 构建多语言站点，排查语言切换或输出合并问题 |
| `bukit-plugins-debug` | 内置插件、进程协议插件、生命周期、增量构建、性能诊断与自定义插件开发 | 插件不运行、输出异常、增量构建行为异常，或构建性能退化 |
| `bukit-deploy` | GitHub Pages 部署、`bukit deploy`、部署配置、环境变量与 CI/CD 设置 | 发布 Bukit 站点到 GitHub Pages，或排查部署失败 |
| `bukit-clone` | 从浏览器抽取到主题生成和验证的网站设计克隆流水线 | 将现有网站的视觉设计克隆或复刻为 Bukit 主题 |
| `bukit-seo` | 通过 `site.seo`、渲染模式、front matter SEO 字段、Open Graph、Twitter Card、JSON-LD、sitemap、robots.txt、audit、diff 实现传统 SEO | 设置 SEO 元数据或解决 `seo.*` 诊断 |
| `bukit-geo` | 通过 `llms.txt`、`llms-full.txt`、AI 爬虫规则、FAQ/HowTo 结构化数据、GEO Score 与诊断实现生成式引擎优化 | 面向 ChatGPT Search、Perplexity、Google AI Overviews、Bing Copilot 等 AI 搜索引擎优化 Bukit 站点 |
| `bukit-preview` | 本地预览服务器行为、`dist/` 服务、MIME 类型、预览模式禁用统计、host/port 配置与端口冲突处理 | 构建后启动或排查 `bukit preview` |
| `bukit-dev` | HMR 开发服务器、文件监听、debounce、增量重建与浏览器实时刷新 | 启动 `bukit dev`、热重载、watch mode，或排查开发服务器问题 |
| `bukit-webhook` | 认证 webhook 监听器、Notion 风格构建触发、GitHub `repository_dispatch`、token 校验、限流与 IP 白名单 | 设置 Notion 到 GitHub 的自动构建触发，或排查 webhook 安全问题 |
| `theme-component-system` | `theme.yaml` V2、sections、components、page templates、data bindings、tokens、catalog、schema、page composer 与继承链 | 构建、检查或调试模块化、AI 可消费的 Bukit 主题 |

## 推荐加载顺序

1. 当任务已经明确是 Bukit 任务时，先看 `using-bukit`
2. 凡是涉及命令执行，先使用 `bukit-cli-reference`
3. 涉及 `site.yaml`、内容结构、插件或部署设置时，加载 `bukit-config`
4. 表现层任务使用 `bukit-theme`、`bukit-design-tokens`、`theme-component-system` 和 `bukit-templating`
5. 内容、URL、语言和可发现性任务使用 `bukit-notion`、`bukit-routing`、`bukit-i18n`、`bukit-seo` 或 `bukit-geo`
6. 运维类流程使用 `bukit-preview`、`bukit-dev`、`bukit-deploy`、`bukit-webhook`、`bukit-clone` 或 `bukit-plugins-debug`

一条通用工作流可以概括为：

```text
using-bukit
  -> bukit-cli-reference
  -> bukit-config
  -> 按任务选择领域 skill
  -> 需要时进入验证与排障 skill
```

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

### 部署到 GitHub Pages

1. `using-bukit`
2. `bukit-deploy`
3. `bukit-config`
4. `bukit-cli-reference`

### 配置 SEO

1. `using-bukit`
2. `bukit-seo`
3. `bukit-config`
4. `bukit-cli-reference`

### 配置面向 AI 搜索的 GEO

1. `using-bukit`
2. `bukit-geo`
3. `bukit-config`
4. `bukit-cli-reference`

### 克隆网站设计

1. `using-bukit`
2. `bukit-clone`
3. `bukit-theme`
4. `bukit-templating`
5. `bukit-cli-reference`

### 构建设计系统

1. `using-bukit`
2. `bukit-design-tokens`
3. `bukit-theme`
4. `bukit-config`

### 根据 schema 生成模板

1. `using-bukit`
2. `bukit-content-to-template`
3. `bukit-config`
4. `bukit-templating`
5. `bukit-design-tokens`

### 构建组件化主题

1. `using-bukit`
2. `theme-component-system`
3. `bukit-theme`
4. `bukit-templating`

### 本地预览或 HMR 开发

1. `using-bukit`
2. `bukit-preview` 或 `bukit-dev`
3. `bukit-cli-reference`

### 配置自动 webhook 构建

1. `using-bukit`
2. `bukit-webhook`
3. `bukit-notion`
4. `bukit-cli-reference`

## Bukit 最小体验流程

本仓库本身不是 Bukit 站点，不能在仓库根目录直接执行 `bukit build`、`bukit preview` 或 `bukit dev`。如果你想体验 Bukit 的最小工作流，请在真实站点目录中执行：

```bash
bukit version
bukit init ./my-site --provider markdown
cd my-site
bukit build
bukit preview
```

补充说明：

- `bukit build`、`bukit preview` 和 `bukit dev` 需要在包含 `site.yaml` 的站点根目录执行
- 默认输出目录通常是 `dist`
- 使用 Notion 作为内容源时，通常还需要配置 `NOTION_TOKEN`
- 部署和 webhook 流程通常需要 GitHub 相关环境变量或 token
- Windows 下如果直接调用可执行文件，常见形式是 `.\bukit.exe version` 或 `& .\bukit.exe version`

## 目录与平台文件

- `skills/skills-index.yaml` 是主要机器可读目录；当 skill 清单或工作流链路变化时，应先更新它
- `skills/skills-index.json` 是供工具使用的生成版 JSON 目录
- `skills/plugin.json` 列出打包的 skill 文件路径和可选依赖
- `skills/CLAUDE.md`、`skills/AGENTS.md`、`skills/GEMINI.md` 和 `skills/copilot-instructions.md` 将同一套 skill 边界适配到不同 Agent 环境
- `skills/scripts/validate-skills.sh` 检查 manifest 路径、必需 front matter、触发说明、常见错误章节和硬编码工具名问题
- `skills/scripts/generate-index-json.sh` 从 YAML 源重新生成 JSON 目录数据

## 维护约定

- 每个 skill 固定放在 `skills/<skill-name>/SKILL.md`
- `description` 用来描述触发条件与任务边界，不写泛化营销介绍
- 命令执行规则与 CLI 输出解释统一收敛到 `bukit-cli-reference`
- 主题路径、配置字段、CLI 参数、诊断代码与工作流链路应与 Bukit 实际行为保持一致
- 新增 Bukit 能力时，优先判断是扩充现有 skill 还是新增独立 skill
- skill 清单变化时，三种语言的 README 应一起更新
- 修改 skills、manifest 或生成目录后，运行校验脚本

## 文档说明

- 默认英文入口：[`README.md`](./README.md)
- 中文说明：[`README.zh-CN.md`](./README.zh-CN.md)
- 马来文说明：[`README.ms.md`](./README.ms.md)
- 所有技能文档位于 [`skills/`](./skills)
