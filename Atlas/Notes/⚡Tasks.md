---
up:
  - "[[🏠 Home]]"
related:
  - "[[Efforts.base]]"
date: 2026-04-26
---

# ⚡Tasks

> [!info]
> 这里是轻量 GTD 控制台：今天执行放 Daily，项目推进放 Project，周期复盘放 Weekly/Monthly。
>
> 规则：
> - 今日任务：直接放 Daily 的 `☑️Tasks`，只结转这个区块里的未完成任务。
> - 项目任务：放 `Efforts/Projects` 的项目页。
> - 周/月任务：放 Weekly/Monthly，用来承接复盘和周期目标。
> - Inbox 只收集未分类材料和想法，不作为任务来源。
> - 习惯、健康、End-of-Day Checklist 不参与 Daily 结转。

## 今日执行：最近一篇日记未完成

```dataviewjs
const dailyPages = dv.pages('"Calendar/Daily"')
  .where(p => p.file.tasks && p.file.tasks.some(t => !t.completed))
  .sort(p => p.file.name, 'desc')
  .array();

if (dailyPages.length === 0) {
  dv.paragraph("暂无未完成的日记任务。");
} else {
  const latest = dailyPages[0];
  const openTasks = latest.file.tasks.filter(t => !t.completed);
  dv.paragraph(`最近来源：${latest.file.link}`);
  dv.taskList(openTasks, false);
}
```

## 项目推进

```dataview
TASK
FROM "Efforts/Projects"
WHERE !completed
GROUP BY file.link
SORT file.mtime DESC
```

## 周复盘任务

```dataviewjs
const allWeekly = dv.pages('"Calendar/Weekly"')
  .where(p => p.file.tasks && p.file.tasks.some(t => !t.completed))
  .sort(p => p.file.name, 'desc')
  .array();

if (allWeekly.length === 0) {
  dv.paragraph("暂无未完成的周记任务。");
} else {
  const target = allWeekly[0];
  const openTasks = target.file.tasks.filter(t => !t.completed);
  dv.paragraph(`周记来源：${target.file.link}`);
  dv.taskList(openTasks, false);
}
```

## 月复盘任务

```dataviewjs
const allMonthly = dv.pages('"Calendar/Monthly"')
  .where(p => p.file.tasks && p.file.tasks.some(t => !t.completed))
  .sort(p => p.file.name, 'desc')
  .array();

if (allMonthly.length === 0) {
  dv.paragraph("暂无未完成的月记任务。");
} else {
  const target = allMonthly[0];
  const openTasks = target.file.tasks.filter(t => !t.completed);
  dv.paragraph(`月记来源：${target.file.link}`);
  dv.taskList(openTasks, false);
}
```

## 年度任务

```dataviewjs
const allYearly = dv.pages('"Calendar/Yearly"')
  .where(p => p.file.tasks && p.file.tasks.some(t => !t.completed))
  .sort(p => p.file.name, 'desc')
  .array();

if (allYearly.length === 0) {
  dv.paragraph("暂无未完成的年记任务。");
} else {
  const target = allYearly[0];
  const openTasks = target.file.tasks.filter(t => !t.completed);
  dv.paragraph(`年记来源：${target.file.link}`);
  dv.taskList(openTasks, false);
}
```

## 来源统计：哪里积压最多

```dataview
TABLE length(rows) AS 未完成数
FROM ""
FLATTEN file.tasks AS t
WHERE !t.completed
AND !contains(file.folder, "x")
GROUP BY file.folder
SORT length(rows) DESC
```

## 其他未完成

```dataview
TASK
FROM ""
WHERE !completed
AND !contains(file.folder, "x")
AND !contains(file.folder, "Calendar/Daily")
AND !contains(file.folder, "Calendar/Weekly")
AND !contains(file.folder, "Calendar/Monthly")
AND !contains(file.folder, "Calendar/Yearly")
AND !contains(file.folder, "Efforts/Projects")
AND !contains(file.folder, "+")
GROUP BY file.link
SORT file.mtime DESC
```
