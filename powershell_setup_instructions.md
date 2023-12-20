
# PowerShell 7 自动补全功能配置教程

PowerShell 7 支持通过 PSReadLine 模块增强自动补全和命令历史功能。以下是如何安装 PSReadLine 并配置自动补全的步骤。

## 安装 PSReadLine 模块

打开 PowerShell 7 并运行以下命令以安装最新版本的 PSReadLine（如果尚未安装）：

```powershell
Install-Module -Name PSReadLine -AllowPrerelease -Scope CurrentUser -Force -SkipPublisherCheck
```

## 配置自动补全功能

编辑 PowerShell 的配置文件（通常是 `$PROFILE` 文件）以启用和配置自动补全功能。

### 打开配置文件

如果配置文件不存在，以下命令将会创建一个：

```powershell
if (!(Test-Path -Path $PROFILE)) { New-Item -Type File -Path $PROFILE -Force }
notepad.exe $PROFILE
```

### 添加自动补全配置

将以下配置添加到 `$PROFILE` 文件中，然后保存并关闭文件：

```powershell
Import-Module PSReadLine
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineKeyHandler -Key Tab -Function MenuComplete
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadLineOption -ShowToolTips
```

关闭并重新打开 PowerShell 以使更改生效。

### 启用历史命令的上下键导航

添加以下键绑定以启用历史命令的上下键导航：

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward
```

### 设置历史搜索时光标移动到行尾

如果希望在输入命令时显示与已输入内容匹配的历史命令，可以添加：

```powershell
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
```

## 注意事项

编辑 `$PROFILE` 文件时请小心操作，因为错误的配置可能会影响 PowerShell 的正常使用。如需恢复默认设置，只需从 `$PROFILE` 文件中移除这些配置或注释掉即可。
