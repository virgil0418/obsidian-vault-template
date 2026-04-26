# Atlas Log

本文件是知识库重要 ingest、query、promote、lint、maintain 操作的追加式维护时间线。

日志标题格式：

```md
## [YYYY-MM-DD] ingest | 标题
## [YYYY-MM-DD] query | 标题
## [YYYY-MM-DD] promote | 标题
## [YYYY-MM-DD] lint | 标题
## [YYYY-MM-DD] maintain | 标题
```

## [2026-04-26] maintain | 建立 agent 维护型知识库 schema

- 新增 `AGENTS.md`，作为本仓库的 agent 行为 schema。
- 明确 `Atlas/Sources` 是来源材料区，`Atlas/Notes` 是稳定知识区，`Atlas/Maps` 是导航结构区。
- 确立 Maps + Bases + frontmatter 共同承担索引能力，不强制要求 `index.md`。

## [2026-04-26] maintain | 调整 schema 为中文优先

- 将 `AGENTS.md` 改为中文优先表达，保留必要英文术语。
- 将 Base 视图名称和模板中的 Notes/Sources 标题调整为中文优先。

## [2026-04-27] maintain | 将 x 明确为控制面层

- 更新 LLM Wiki 映射，将 schema 实现从 `x/Templates` 扩展为整个 `x` 控制面层。
- 同步 `AGENTS.md` 与知识库总图，明确 `x` 支撑模板、按钮、附件和样式，但不作为 canonical 知识层。

## [2026-04-27] maintain | 建立 WORK 与 LESSON 记录

- 新增 `WORK.md`，用于记录 agent 拆解的工作项、状态、验证结果和决策。
- 新增 `LESSON.md`，用于沉淀 agent 维护知识库时的可复用经验。
- 同步 `AGENTS.md` 与知识库总图，明确两者是执行控制文档，不替代 canonical 知识层。
