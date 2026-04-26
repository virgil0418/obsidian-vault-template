---
page_type: note
note_type: background
status: stable
summary: 说明 LLM Wiki 思路如何被翻译到当前 Obsidian 仓库结构中。
up:
  - "[[🏠 Home]]"
related:
  - "[[⚡Tasks]]"
sources: []
date: 2026-04-26
updated: 2026-04-26
---
# LLM Wiki 到当前仓库的映射

这篇 note 是背景说明，用来记录当前仓库改造的设计来源。它不是 agent 的最高操作规则；agent 执行任务时应以仓库根目录的 `AGENTS.md` 为准。

## 核心理解

LLM Wiki 的重点不是固定目录名，而是让知识库具备几种能力：保存来源、沉淀稳定知识、提供索引入口、规定 agent 工作流、记录维护历史。

当前仓库已经是 Obsidian 笔记库，所以不照搬 `raw/`、`wiki/`、`index.md` 这些文件名，而是把这些能力翻译到现有结构里。

## 概念映射

| LLM Wiki 概念 | 当前仓库实现 |
| --- | --- |
| raw sources | `Atlas/Sources` |
| wiki | `Atlas/Notes` + `Atlas/Maps` |
| schema | `AGENTS.md` + `x/Templates` + frontmatter 约定 |
| index | `Atlas/Maps` + `Atlas/Bases` + frontmatter |
| log | `Atlas/log.md` |
| ingest / query / lint | `AGENTS.md` 中定义的工作流 |

## 为什么不新增 raw

当前仓库已经有 `Atlas/Sources/Books`、`Atlas/Sources/Clippings`、`Atlas/Sources/Courses`。为了减少目录概念，直接让 `Atlas/Sources` 承担来源材料区职责。

这里可以放：

- 网页剪藏
- 书摘
- 课程笔记
- 语音转文字
- PDF 转 Markdown
- 会议记录
- 其他原始或近原始材料

Agent 默认不改写这些来源正文，而是把可复用结论提炼到 `Atlas/Notes`。

## 为什么不强制 index.md

Obsidian 已经有更自然的索引系统：

- `Atlas/Maps` 提供人工策展的 MOC 和主题地图。
- `Atlas/Bases` 提供动态表格和过滤视图。
- frontmatter 提供可查询的结构化字段。
- Home 页面提供人类入口。

因此，本仓库需要的是“索引能力”，不一定需要一个叫 `index.md` 的文件。

## Schema 的实现

Schema 不只是一份说明文档，而是一组让人和 agent 都能稳定协作的约束：

- `AGENTS.md` 说明目录语义、读写边界和工作流。
- `x/Templates/TEMPLATE-Notes.md` 规定知识卡的默认形状。
- `x/Templates/TEMPLATE-Map.md` 规定地图页的默认形状。
- frontmatter 字段让 Base 和 agent 可以识别页面类型。

`Atlas/Sources` 不设置模板，因为它保留原始材料，不应该被迫改造成统一格式的 wiki 页面。
