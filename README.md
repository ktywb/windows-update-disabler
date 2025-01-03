# Windows 更新禁用工具

![](https://i.imgur.com/pGsWaOt.png '出现了问题')

⚡ 一键禁用自动更新的工具，无需担心后台残留运行的程序。

> [!警告]  
> 在运行此脚本之前，请确保 Windows 已完全更新，并且当前没有正在安装或下载的更新！中断更新可能会导致 Windows 系统损坏！

## 使用方法

### 非常简单！

1. **克隆或下载：**

    - 使用 `git clone https://github.com/tsgrgo/windows-update-disabler.git` 克隆此仓库，或者下载 ZIP 文件并解压。

2. **检查是否有正在进行的更新：**

    - 确保当前没有更新正在安装。进入 **设置 > 更新和安全 > Windows 更新** 检查更新状态。

3. **运行脚本：**

    - 执行 `disable updates.bat`。此操作将禁用自动 Windows 更新。

4. **重新启用更新（可选）：**
    - 如果需要再次启用自动更新，运行 `enable updates.bat`。该脚本完全逆转 `disable updates.bat` 所做的所有更改。

## 手动更新方法

建议定期更新以保证安全性。手动更新步骤如下：

1. **启用更新：**

    - 运行 `enable updates.bat` 以重新启用 Windows 更新。

2. **执行更新：**

    - 进入 **设置 > 更新和安全 > Windows 更新** 并安装可用的更新。

3. **再次禁用更新：**
    - 更新完成后，运行 `disable updates.bat` 再次禁用自动更新。

## 临时启用更新服务

某些应用（如 Microsoft Store）依赖于 Windows 更新服务。临时启用服务的方法如下：

1. **启用更新服务：**

    - 运行 `use update service.bat` 以重新启用 Windows 更新服务。

2. **使用依赖应用：**

    - 现在可以使用需要更新服务的应用程序。

3. **再次禁用更新服务：**
    - 完成后，运行 `disable updates.bat` 再次禁用更新服务。

## 它的工作原理

脚本通过以下操作禁用自动更新：

-   禁用 **Windows 更新服务 (wuauserv)**。
-   禁用 **更新协调器服务 (UsoSvc)**。
-   禁用 **Windows 更新修复服务 (WaaSMedicSvc)**。
-   禁用所有与更新相关的计划任务。
-   应用注册表更改以阻止自动更新。

## 为什么需要 PsExec？

某些服务和任务受到用户账户保护，必须以更高的系统权限进行修改。PsExec 允许脚本以必要的权限运行命令，从而绕过这些限制。

PsExec 是微软官方 Sysinternals 套件的一部分。更多信息请访问：https://docs.microsoft.com/zh-cn/sysinternals/downloads/psexec
