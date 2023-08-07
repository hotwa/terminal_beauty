# Terminal

[github repository](https://github.com/craftzdog/dotfiles-public)

## [Windows 11](https://zhuanlan.zhihu.com/p/137595941)

profile path : `C:\Users\%username%\Documents\PowerShell`

[powershell7](https://github.com/PowerShell/PowerShell/releases)

- [Scoop](https://scoop.sh/) - A command-line installer
- [Git for Windows](https://gitforwindows.org/)
- [Oh My Posh](https://ohmyposh.dev/) - Prompt theme engine
- [Terminal Icons](https://github.com/devblackops/Terminal-Icons) - Folder and file icons
- [PSReadLine](https://docs.microsoft.com/en-us/powershell/module/psreadline/) - Cmdlets for customizing the editing environment, used for autocompletion
- [z](https://www.powershellgallery.com/packages/z) - Directory jumper
- [PSFzf](https://github.com/kelleyma49/PSFzf) - Fuzzy finder

## 安装 Powershell 插件

```shell
# 1. 安装 PSReadline 包，该插件可以让命令行很好用，类似 zsh
Install-Module -Name PSReadLine  -Scope CurrentUser

# 2. 安装 posh-git 包，让你的 git 更好用
Install-Module posh-git  -Scope CurrentUser

# 3. 安装 oh-my-posh 包，让你的命令行更酷炫、优雅
Install-Module oh-my-posh -Scope CurrentUser

Install-Module -Name z
```

```powershell
notepad.exe $Profile
```

## install oh-my-posh

```shell
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
# 或者
iwr -useb get.scoop.sh | iex
# dir (Get-Command oh-my-posh).Source
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
# download font https://www.nerdfonts.com/font-downloads
# Meslo LG M Regular Nerd Font Complete Mono Windows Compatible
# Preview
Get-PoshThemes
# set POSH_THEMES_PATH ENV and edit notepad $PROFILE 
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH/主题名称.omp.json" | Invoke-Expression
```

## install offline

```shell
# 有可能失败.先离线下载instll.ps1
wget -c https://raw.githubusercontent.com/scoopinstaller/install/master/install.ps1

# 执行安装脚本--以管理员执行
iex .\install.ps1 -RunAsAdmin

# 实际执行
iex "E:\aliyun\Desktop\install.ps1"
```
