---
up:
  - "[[Coding]]"
related:
date: 2025-07-21
---


[[Linux basic commands]]
## Ubuntu
包管理器 apt

## 备份
```
备份目录 /home/user 和 /etc 到 /backup/ 目录，生成压缩包 sudo tar -czvPf /backup/system-backup-$(date +%Y%m%d).tar.gz /home/user /etc # 参数说明 # c: 创建归档 z: gzip压缩 v: 显示过程 P: 保留绝对路径 f: 指定输出文件 # $(date +%Y%m%d): 自动添加日期后缀，避免覆盖 # 恢复命令（先进入目标目录，或指定路径） sudo tar -xzvPf /backup/system-backup-20251222.tar.gz -C /
```