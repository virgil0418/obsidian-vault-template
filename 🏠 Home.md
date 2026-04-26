---
cssclasses:
  - hide-properties
banner: "[[banner.png]]"
banner_position: "10"
---
# 🏠 Home

> [!info]
> 这是一个空骨架模板。文件夹负责内容类型，链接和属性负责关系。

> [!abstract] 任务管理
> [[⚡Tasks|全局任务看板]] · [[Efforts.base|行动总览]]

```columns
id: home-actions
===
`button-daily-note` `button-weekly` `button-monthly` `button-unique`
```

> [!todo] 今日执行清单
> 最近一篇日记中的未完成任务（断更也可见）：
> ```dataviewjs
> const dailyPages = dv.pages('"Calendar/Daily"')
>   .where(p => p.file.tasks && p.file.tasks.some(t => !t.completed))
>   .sort(p => p.file.name, 'desc')
>   .array();
>
> if (dailyPages.length === 0) {
>   dv.paragraph("暂无未完成的日记任务。");
> } else {
>   const latest = dailyPages[0];
>   const openTasks = latest.file.tasks.filter(t => !t.completed);
>   dv.paragraph(`最近来源：${latest.file.link}`);
>   dv.taskList(openTasks, false);
> }
> ```
>
> 项目中的未完成（Top 8）：
> ```dataview
> TASK
> FROM "Efforts/Projects"
> WHERE !completed
> GROUP BY file.link
> SORT file.mtime DESC
> LIMIT 8
> ```
> 全量看板：[[⚡Tasks]]

```columns
id: home-sections
===
## 💪 行动
[[Efforts.base|行动总览 Efforts]]

[[Areas.base|长期领域 Areas]]

[[Projects.base|短期项目 Projects]]

===
## 📅 日历
[[Calendar.base|日历 Calendar]]

[[TEMPLATE-Daily|Daily Template]]

[[TEMPLATE-Weekly|Weekly Template]]

[[TEMPLATE-Monthly|Monthly Template]]

===
## 📝 笔记
[[知识库总图|知识库总图]]

[[Notes.base|原子笔记 Notes]]

[[Maps.base|主题地图 Maps]]

[[TEMPLATE-Notes|Note Template]]

[[TEMPLATE-Map|Map Template]]

===
## 📖 资源
[[Books Database.base|书籍 Books]]

[[Clippings.base|摘录 Clippings]]

[[Courses.base|课程 Courses]]
```

> [!blue] 文件索引：[[PDF.base|PDF]] · [[IMAGES.base|Images]] · [[TEMPLATES.base|Templates]] · [[+.base|Inbox]]
