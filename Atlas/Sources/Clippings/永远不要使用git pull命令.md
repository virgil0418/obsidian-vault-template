---
up:
  - "[[Github]]"
related:
date: 2026-01-11
url: https://www.bilibili.com/video/BV1N1xyzDEjL
---
`git pull`会生成一堆无意义的合并记录

`git pull --rebase`会先拉取别人的记录，再把自己的记录放上去，形成线性的记录，更加直观
如果出现冲突 `git rebase abort`撤销拉取操作

然后再用git pull正常拉取，解决冲突