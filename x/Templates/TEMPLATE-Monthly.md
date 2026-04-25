<%*
let d = moment(tp.file.title, "YYYY-MM");
let monthStart = d.clone().startOf('month');
let monthEnd = d.clone().endOf('month');
-%>
---
year: '[[<% d.format("YYYY") %>]]'
collections: "[[Monthly]]"
month_start: '<% monthStart.format("YYYY-MM-DD") %>'
month_end: '<% monthEnd.format("YYYY-MM-DD") %>'
---

# MONTHLY NOTE

## 本月目标

-

## ☑️Tasks

- [ ]

## 本月 Daily 未完成

```dataview
TASK
FROM "Calendar/Daily"
WHERE !completed
AND date(file.name) >= date(this.month_start)
AND date(file.name) <= date(this.month_end)
GROUP BY file.link
SORT file.name ASC
```

## 项目盘点

```dataview
TABLE status, rank
FROM "Efforts/Projects"
WHERE status != "sleeping"
SORT rank DESC
```

## 月末复盘

### 完成了什么


### 哪些任务应该取消或下沉


### 下月要推进什么

- [ ]
