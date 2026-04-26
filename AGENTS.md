# AGENTS.md

这个仓库是一个由人类和 agent 共同维护的 Obsidian 知识库。

人类主要使用 Obsidian 捕捉、浏览、连接和复盘知识。Agent 负责辅助分流材料、提炼可复用知识、维护链接关系，并定期检查知识库健康状态。

本文件是本仓库中 agent 行为的唯一权威 schema。未来 agent 不需要读过任何外部设计文档，也应能仅凭本文件理解如何工作。

## 仓库目标

本仓库的目标是让有用知识持续积累，而不是停留在一次性聊天或散落文件中。

- 人类提供来源、问题、判断和方向。
- Agent 负责整理、总结、交叉链接、晋升内容和执行 lint。
- 仓库应同时适合人类在 Obsidian 中阅读，也适合 agent 通过目录、模板、frontmatter、MOC 和 Base 稳定维护。

## 目录语义

按内容职责分流，不按方便程度乱放。

- `+`：临时收件箱和待分流区。用于未分类材料、粗糙草稿、临时分析、还没有明确归属的笔记。这里不是 canonical 知识层。
- `Atlas/Sources`：来源材料区。用于原始或近原始材料，例如网页剪藏、书摘、课程笔记、语音转文字、PDF 转 Markdown、会议记录和外部证据。
- `Atlas/Notes`：稳定知识区。用于可复用概念、方法、原则、案例、标准答案和综合结论。
- `Atlas/Maps`：导航和结构区。用于 MOC、主题地图、领域地图、阅读路径和人类入口页。
- `Atlas/Bases`：Obsidian Base 视图区。用于基于 frontmatter 和文件属性生成动态索引、过滤视图和健康检查视图。
- `Calendar`：时间上下文。用于日记、周记、月记、季度/年度笔记、周期复盘和时间范围内的追踪。
- `Efforts`：行动和交付层。用于项目、领域、目标、项目任务和执行上下文。
- `x`：知识库基础设施。用于模板、附件、隐藏模板、按钮、CSS snippets 和其他支持文件。

## 来源保护规则

`Atlas/Sources` 是本仓库的 source of truth 区域。

- 默认把来源文件视为只读材料。
- 不要把来源正文重写成总结。
- 不要为了让长来源“看起来像 wiki 页面”而重构其正文。
- 不要创建 Source 模板；来源文件可以保留采集时的原始形态。
- 只有在有助于分流或 Base 视图时，才可以补充或规范少量 frontmatter；不得破坏来源正文。
- 如果来源中包含可长期复用的知识，应提炼到 `Atlas/Notes`，并回链到来源。
- 如果来源改变了主题结构，应更新或创建 `Atlas/Maps` 页面。

## 页面类型

使用 `page_type` 让页面可以被 Base 和 agent 识别。

- `source`：位于 `Atlas/Sources` 的原始或近原始材料。
- `note`：位于 `Atlas/Notes` 的可复用知识卡。
- `map`：位于 `Atlas/Maps` 的 MOC 或导航页。
- `project`：位于 `Efforts` 的项目或行动材料。
- `calendar`：位于 `Calendar` 的时间范围笔记。
- `inbox`：位于 `+` 的待分流材料。
- `template`：位于 `x/Templates` 或 `x/Hidden Templates` 的模板或支持页面。
- `system`：操作性文件，例如本文件、日志、Base 定义和知识库支持文件。

如果已有页面缺少 `page_type`，不要为了合规批量改全库。只有在真实工作流中触碰页面时，才补充或更新 frontmatter。

## Frontmatter 约定

`Atlas/Notes` 页面建议使用以下最小结构：

```yaml
page_type: note
note_type:
status: seed
summary:
up:
related:
sources:
date:
updated:
```

`Atlas/Maps` 页面建议使用以下最小结构：

```yaml
page_type: map
map_type:
status: active
summary:
up:
related:
date:
updated:
```

`Atlas/Sources` 页面不需要模板。如果来源文件天然带有 frontmatter，或确实需要轻量分流字段，可使用以下简单字段：

```yaml
page_type: source
source_type:
status:
date:
url:
```

字段含义：

- `status`：生命周期状态，例如 `seed`、`active`、`stable`、`archived`、`unread`、`reading`、`ingested`。
- `summary`：一句话说明这个页面为什么存在。
- `up`：上级地图、领域或更大的主题。
- `related`：相邻、同级或相关页面。
- `sources`：支撑某个 note 的来源页面。
- `date`：创建日期或来源日期；已知时填写。
- `updated`：最近一次有意义的知识更新日期。

## 导航和索引

本仓库不要求传统的 `index.md`。

索引能力由以下部分共同承担：

- `🏠 Home.md`：人类首页。
- `Atlas/Maps`：人工策展的 MOC 和主题导航。
- `Atlas/Bases`：动态表格和过滤视图。
- frontmatter 字段：结构化查询基础。
- 全文搜索：需要时使用 `rg` 等工具。

Agent 导航协议：

1. 先读本 `AGENTS.md`。
2. 使用 `🏠 Home.md` 和相关 `Atlas/Maps` 页面理解方向。
3. 需要动态目录时，查看 `Atlas/Bases` 定义，或基于 frontmatter 搜索。
4. 稳定回答优先参考 `Atlas/Notes` 和 `Atlas/Maps`。
5. 需要证据、原文表述或核实时，再读取 `Atlas/Sources`。
6. `+` 只能作为待分流上下文，不要当作 canonical 知识。
7. 涉及项目和行动时读取 `Efforts`；涉及时间脉络时读取 `Calendar`。

## 工作流

### Ingest

当新来源材料或新笔记进入仓库时使用。

1. 判断材料应留在 `+` 还是进入 `Atlas/Sources`。
2. 原始材料、语音转文字、PDF 转 Markdown、网页剪藏和书摘应保留在 `Atlas/Sources`。
3. 不改写来源正文。
4. 将稳定、可复用的知识提炼到 `Atlas/Notes`。
5. 只有当新材料改变导航或主题结构时，才更新或创建 `Atlas/Maps`。
6. 在新 note、相关 map 和支撑 sources 之间建立链接。
7. 重要 ingest 追加记录到 `Atlas/log.md`。

### Query

当用户基于知识库提问时使用。

1. 从本文件开始，再通过 Home、Maps、Bases/frontmatter 和搜索定位相关页面。
2. 优先基于 `Atlas/Notes` 和 `Atlas/Maps` 回答。
3. 当答案需要证据，或稳定 note 缺失时，再读取 `Atlas/Sources`。
4. 如果答案稳定且可复用，创建或更新 `Atlas/Notes` 页面。
5. 如果答案只是临时分析或任务相关内容，默认留在聊天中；只有用户要求保存时才放入 `+`。
6. 只有当 query 创建或实质更新了仓库内容时，才记录日志。

### Promote

当需要把临时内容或上下文内容晋升到 wiki 层时使用。

1. 从 `+`、`Calendar`、`Efforts` 或一次 query 答案中识别可复用知识。
2. 判断内容应进入 `Atlas/Notes`、`Atlas/Maps`、`Efforts`，还是继续留在原处。
3. 只有当内容脱离原日期或任务语境后仍然有价值时，才晋升到 `Atlas/Notes`。
4. 只有当内容承担导航、结构或主题关系组织作用时，才晋升到 `Atlas/Maps`。
5. 晋升后补齐必要 frontmatter、链接和来源引用。
6. 有意义的 promote 追加记录到 `Atlas/log.md`。

### Lint

用于检查知识库健康状态。

检查重点：

- `+` 中是否有长期未分流材料。
- 来源文件是否被改写成综合知识页。
- `Atlas/Notes` 是否混入了大量原始材料。
- 重要主题是否缺少或存在过期的 `Atlas/Maps` 覆盖。
- Notes 或 Maps 是否缺少有用的 `summary`、`up` 或 `related` 字段。
- Base 视图依赖的字段是否填写不一致。
- 是否存在重复 note、孤儿 note 和断链。
- `Calendar` 或 `Efforts` 中是否隐藏了应晋升到 `Atlas/Notes` 的稳定知识。

Lint 结果写到最适合当前任务的位置。如果 lint 推动了实质性修改，应追加记录到 `Atlas/log.md`。

## 日志规则

使用 `Atlas/log.md` 作为机器友好的维护时间线。

追加日志时使用以下标题格式：

```md
## [YYYY-MM-DD] ingest | 标题
## [YYYY-MM-DD] query | 标题
## [YYYY-MM-DD] promote | 标题
## [YYYY-MM-DD] lint | 标题
## [YYYY-MM-DD] maintain | 标题
```

日志应简短。除非修正最近条目的明显笔误，不要重写旧日志。

Weekly 笔记可以包含面向人类的复盘，但不能替代 `Atlas/log.md`。

## 编辑规则

- 保留用户改动，绝不回滚无关编辑。
- 不要把 `Atlas/Sources` 当作 agent 综合稿的草稿区。
- 不要把 `+` 当作 canonical 知识层。
- 优先更新已有 note 或 map，避免创建近重复页面。
- Obsidian 链接应对人类有用；能提升导航清晰度时使用 `[[页面名]]`。
- 模板保持轻量，不添加 Source 模板。
- 修改结构时，同步更新相关 Maps、Bases、模板或本 schema，确保未来 agent 能遵循同一套规则。
