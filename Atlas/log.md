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
