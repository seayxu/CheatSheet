---
title: dotnet-install scripts reference
description: dotnet-install scripts reference
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 59b9c456-2bfd-4adc-8202-a1c6a0a6c787
---

dotnet-install scripts reference
================================

dotnet-install 脚本参考
================================

## NAME
## 名称
dotnet-install.ps1 | dotnet-install.sh - script used to install the Command Line Interface (CLI) tools and shared runtime

dotnet-install.ps1 | dotnet-install.sh - 用于安装命令行界面（CLI）工具的脚本和共享运行时

## SYNOPSIS
## 概要
Windows:

`dotnet-install.ps1 [-Channel] [-Version]
    [-InstallDir] [-Debug] [-NoPath] 
    [-SharedRuntime]`

OS X/Linux:

`dotnet-install.sh [--channel] [--version]
    [--install-dir] [--debug] [--no-path] 
    [--shared-runtime]`

## DESCRIPTION
## 描述
The `dotnet-install` scripts are used to perform a non-admin install of the CLI toolchain and the shared runtime. You can download the scripts from our [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain). 

`dotnet-install` 安装脚本用来执行非管理员安装 CLI 工具链和共享运行时。你可以从我们的 [CLI GitHub repo](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain) 下载脚本。

Their main use case is to help with automation scenarios and non-admin installations. There are two scripts, one for PowerShell that works on Windows and a bash script that works on Linux/OS X. They both have the same behavior. Bash script also "understands" PowerShell switches so you can use them across the board. 

其主要用于帮助自动化场景和非管理员安装。有两个脚本，一个是在 Windows 上工作的 PowerShell 和另一个在 Linux/OS X 上工作的 bash 脚本。他们两者有同样的行为。Bash 脚本也可以“理解”为 PowerShell 的切换，因此你可以全线使用他们。

Installation scripts will download the ZIP/tarball file from the CLI build drops and will proceed to install it in either the default location or in a location specified by `--install-dir`. By default, the installation script 
will download the SDK and install it; if you want to get just the shared runtime, you can specify the `--shared-runtime` argument. 

安装脚本会从 CLI 下载 ZIP/tarball（压缩包）文件生成，并且将可能在默认位置或者在通过 `--install-dir` 指定的位置进行安装。默认情况下，该安装脚本将下载 SDK 和安装它；如果你仅仅想获取共享运行时，你可以指定 `--shared-runtime` 参数。

By default, the script will add the install location to the $PATH for the current session. This can be overridden if the `--no-path` argument is used. 

默认情况下，安装脚本将安装位置添加到当前会话的 $PATH 中。这可以被覆盖，如果使用 `--no-path` 参数。

Before running the script, please install all the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

在运行脚本之前，请安装所有的必须 [依赖](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。

You can install a specific version using the `--version` argument. The version needs to be specified as 3-part version (for example 1.0.0-13232). If omitted, it will default to the first global.json file found in the hierarchy above the folder where the script was invoked in that contains the `sdkVersion` property. If that is not present, it will use Latest.

你可以使用 `--version` 参数安装一个指定的版本。该指定的版本需要由 3 部分的版本（例如：1.0.0-13232）。如果忽略，它将默认到被调用脚本的上级文件夹中找到的第一个包含 `sdkVersion`节点的 global.json 文件。如果不存在，它会使用最新的。

You can also use this script to get the SDK or shared runtime debug binaries with debug symbols by using the `--debug` argument. If you do not do this on first install and realize you do need debug symbols later on, you can re-run the script with this argument and the version of the bits you installed. 

你也可以使用这个脚本通过用 `--debug` 参数来获得 SDK 或共享运行时的调试符号的调试二进制文件。如果第一次安装你不这样做，稍后实际上你确实需要调试符号，你可以使用这个参数和你安装的版本重新运行脚本。

## Options
## 选项
Options are different between script implementations. 

不同脚本实现的选项。

### PowerShell (Windows)
`-Channel [CHANNEL]`

Which channel (for example, "future", "preview", "production") to install from. The default value is "Production".

安装的渠道（例如：“future”、“preview”、“production”）。默认版本是“Production”。

`-Version [VERSION]`

Which version of CLI to install; you need to specify the version as 3-part version (i.e. 1.0.0-13232). If omitted, it will default to the first global.json that contains the sdkVersion property; if that is not present, it will use Latest. 	

安装的 CLI 版本。你需要指定由 3 部分组成的版本（例如：1.0.0-13232）。如果忽略，它将默认到被调用脚本的上级文件夹中找到的第一个包含 `sdkVersion`节点的 global.json 文件。如果不存在，它会使用最新的。

`-InstallDir [DIR]`

Path to install to. The directory is created if it doesn't exist. The default value is `%LocalAppData%\.dotnet`.

安装的路径。如果目录不存在则创建它。默认值是 `%LocalAppData%\.dotnet`。

`-Debug`

**true** to indicate that larger packages containing debugging symbols should be used; otherwise, **false**. The default value is **false**.

**true** 表明应该使用包含调试符号的更大包；否则，**false**。默认值是 **false**。

`-NoPath`

**true** to indicate that the prefix/installdir are not exported to the path for the current session; otherwise, **false**. 
The default value is **false**, that is, the PATH is modified. 
This makes the CLI tools available immediately after install. 

**true** 表明前缀/安装目录不导出到当前会话的路径；否则，**false**。默认值是 **false**，那就是，PATH 被修改。这使得 CLI 工具安装后立即可用。

`-SharedRuntime`

**true** to install just the shared runtime bits; **false** to install the entire SDK. The default value is **false**.

**true** 仅仅安装共享运行时。**false** 安装整个 SDK。默认值是 **false**。

### Bash (OS X/Linux)
`--channel [CHANNEL]`

Which channel (for example "future", "preview", "production") to install from. The default value is "Production".

安装的渠道（例如：“future”、“preview”、“production”）。默认版本是“Production”。

`--version [VERSION]`

Which version of CLI to install; you need to specify the version as 3-part version (i.e. 1.0.0-13232). If omitted, it will default to the first global.json that contains the sdkVersion property; if that is not present, it will use Latest. 	

安装的 CLI 版本。你需要指定由 3 部分组成的版本（例如：1.0.0-13232）。如果忽略，它将默认到第一个包含 `sdkVersion`节点的 global.json 文件。如果不存在，它会使用最新的。

`--install-dir [DIR]`

Path to where to install. The directory is created if it doesn't exist. The default value is `$HOME/.dotnet`.

安装的路径。如果目录不存在则创建它。默认值是 `%HOME%/.dotnet`。

`--debug`

**true** to indicate that larger packages containing debugging symbols should be used; otherwise, **false**. The default value is **false**.

**true** 表明应该使用包含调试符号的更大包；否则，**false**。默认值是 **false**。

`--no-path`

**true** to indicate that the prefix/installdir are not exported to the path for the current session; otherwise, **false**. 
The default value is **false**, that is, the PATH is modified. 
This makes the CLI tools available immediately after install.  

**true** 表明前缀/安装目录不导出到当前会话的路径；否则，**false**。默认值是 **false**，那就是，PATH 被修改。这使得 CLI 工具安装后立即可用。

`--shared-runtime`

**true** to install just the shared runtime bits; **false** to install the entire SDK. The default value is **false**.

**true** 仅仅安装共享运行时。**false** 安装整个 SDK。默认值是 **false**。

## EXAMPLES
## 例子

Windows:

```
./dotnet-install.ps1 -Channel Future
```

OS X/Linux:

```
./dotnet-install.sh --channel Future
```

Installs the dev latest version to the default location.

安装最新的开发版本到默认位置。

Windows:

```
./dotnet-install.ps1 -Channel preview -InstallDir C:\cli
```

OS X/Linux:

```
./dotnet-install.sh --channel preview --install-dir ~/cli
```

Installs the latest preview to the specified location.

安装最新的预览版本到指定的位置。