VSCode 相关配置
==============
Author：许滨滨  
Date: 2021年6月13日 16点03分
Desc: 记录使用VSCode之前的一些配置

使用插件
-------

- Chinese (Simplified) Language Pack for Visual Studio Code  
简体中文UI翻译
- Material Icon Theme  
更好看 VSCode 文件夹和文件图标
- GitHub Theme  
GitHub UI 主题

Windows下设置Bash终端
--------------------

1. 使用ctrl + shift + p 快捷键,搜索settings(json),选择"首选项(打开json)"  

2. 在settings(json)中输入"terminal.integrated.shell.windows":“bash.exe路径”  

3. 重启VSCode  
```json
{
    "terminal.integrated.profiles.windows": {
        "PowerShell": {
            "source": "PowerShell",
            "icon": "terminal-powershell"
        },
        "Command Prompt": {
            "path": [
                "${env:windir}\\Sysnative\\cmd.exe",
                "${env:windir}\\System32\\cmd.exe"
            ],
            "args": [],
            "icon": "terminal-cmd"
        },
        "Git Bash": {
            "source": "Git Bash"
        },
        "Bash": {
            "path": "D:\\SotfWare\\04Git\\Git\\bin\\bash.exe"
        }
    }
}
```

中文字体设置
----------

- 文件->首选项->设置->字体->Font Family,设置为”Consolas, '微软雅黑', monospace“