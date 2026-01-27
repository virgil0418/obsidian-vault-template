---
date: 2025-07-21
up:
related:
---

# 软件
## 必备软件
[[Karabiner]]
Raycast 快捷命令
Battery Toolkit 限制充电到80%（75-80）全部选项打开

## 工具
[[OrbStack]]
[[终端]]
[[vscode]]
[[Rime输入法]]

# Mac优化配置
## 禁止更新
1. sudo softwareupdate --schedule off
2. 
```zsh
sudo launchctl disable system/com.apple.softwareupdated
sudo launchctl disable system/com.apple.installerd
```

```zsh
sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticCheckEnabled -bool FALSE

sudo defaults write /Library/Preferences/com.apple.SoftwareUpdate AutomaticDownload -bool FALSE
```
3. etc/hosts文件里加入修改dns屏蔽更新链接

**恢复命令**：
```
sudo launchctl enable system/com.apple.softwareupdated
sudo launchctl enable system/com.apple.installerd
sudo softwareupdate --schedule on sudo defaults delete /Library/Preferences/com.apple.SoftwareUpdate AutomaticCheckEnabled
sudo defaults delete /Library/Preferences/com.apple.SoftwareUpdate AutomaticDownload
```

【禁止Mac更新26Tahoe版本，不怕电脑卡顿，保持15.7】 https://www.bilibili.com/video/BV1mPnPzZE23/?share_source=copy_web&vd_source=f896722c1668e7969f3df6c3688cf6c5

## 关闭Spotlight聚焦显示
关闭
```
sudo mdutil -a -i off
```

开启
```
sudo mdutil -a -i on
sudo mdutil -E /  # 清空并重建索引（可选）
```

