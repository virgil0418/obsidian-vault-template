---
up:
related:
date: 2026-01-16
---
**虚拟环境**
create environment
venv虚拟环境，可以随便装安装包不影响主环境

> [!NOTE]- 实用快捷键
> 打开工程：code + 路径
> 打开指定文件：ctrl + p
> 打开/关闭终端：ctrl + · (1左边的按键) 
> 跳转到行：ctrl + g
> 按单词移动光标：ctrl + 左右
> 选中单词：ctrl + d（重复按可以多选 
> 选中行：ctrl + l （重复按会同时选择下一行）
> 移动行：alt + 上下 
> 格式化代码：ctrl + shift + i
> 跳转到定义：f12
> 查看当前文件符号：ctrl + shift + o
> 剪切/复制当前行：ctrl + x / ctrl + c （什么都不选的时候）
> 切换tab：alt+数字
> 顺序切换tab：ctrl + pageup / pagedown 
> 关闭文件：ctrl+w
> 关闭所有文件：ctrl + k w （ctrl不松手）
> ctrl+b 打开主侧边栏 
> ctrl+shift+e 打开文件管理器
> ctrl+0 焦点聚焦到主侧边栏 
> ctrl+1 焦点聚焦到代码编辑器
> alt + 1234 切换到第1234页 
> ctrl+· 聚焦到终端
> ctrl+shift+space 重新出现函数信息提示 ctrl+\ 添加分屏
> [【必会！VSCode 最实用的快捷键】 ](https://www.bilibili.com/video/BV19jS2YHEZM/?share_source=copy_web&vd_source=f896722c1668e7969f3df6c3688cf6c5)

【宇宙级编辑器VSCode你真的会用么？提高生产力的巨量技巧】 https://www.bilibili.com/video/BV14Z421N7t6/?share_source=copy_web&vd_source=f896722c1668e7969f3df6c3688cf6c5

Settings.json
```
{

"workbench.colorTheme": "Gruvbox Dark Hard",

"editor.fontSize": 18,

//optimization

"files.autoGuessEncoding": true,

//"editor.mouseWheelZoom": true,

//smooth animation

"workbench.list.smoothScrolling": true,

"editor.cursorSmoothCaretAnimation": "on",

"editor.smoothScrolling": true,

"editor.cursorBlinking": "smooth",

//formating

"editor.formatOnPaste": true,

"editor.formatOnType": true,

"editor.formatOnSave": true,

"[jsonc]": {

"editor.defaultFormatter": "esbenp.prettier-vscode",

},

//显示

"editor.guides.bracketPairs": true,

"window.dialogStyle": "custom",

"debug.showBreakpointsInOverviewRuler": true,

"editor.minimap.enabled": false,

//suggest

"editor.acceptSuggestionOnCommitCharacter": false, //关闭输入符号时自动接受建议

"editor.suggest.snippetsPreventQuickSuggestions": false,

"editor.acceptSuggestionOnEnter": "smart",

"editor.suggestSelection": "recentlyUsed",

//code-runner

"code-runner.runInTerminal": true,

"code-runner.saveAllFilesBeforeRun": true,

"code-runner.saveFileBeforeRun": true,

//gitlens

"gitlens.ai.model": "vscode",

"gitlens.ai.vscode.model": "copilot:gpt-4.1",

"security.promptForLocalFileProtocolHandling": false,

"github.copilot.nextEditSuggestions.enabled": true,

"[markdown]": {

"editor.defaultFormatter": "esbenp.prettier-vscode",

},

"editor.fontFamily": "JetBrains Maple Mono",

}
```
