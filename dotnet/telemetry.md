---
title: .NET Core Tools Telemetry
description: .NET Core
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 07/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f2b312bb-f80b-4b0d-9101-93908f06a6fa
---

# .NET Core Tools Telemetry
# .NET Core 工具遥测（应用信息收集）

The .NET Core Tools include a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information. It’s important that the .NET Team understands how the tools are being used so that we can improve them.

.NET Core 工具包含收集使用信息的 [遥测功能](https://github.com/dotnet/cli/pull/2145)。对于 .NET 团队了解如何使用工具以便于可以提升它们是重要的。

The data collected is anonymous and will be published in an aggregated form for use by both Microsoft and community engineers under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).

收集的数据是匿名的，并将发布一个汇总的形式，在 [知识共享署名许可协议](https://creativecommons.org/licenses/by/4.0/) 下供微软和社区工程师使用。

## Scope
## 适用范围

The `dotnet` command is used to launch both apps and the .NET Core Tools. The `dotnet` command itself does not collect telemetry. It is the .NET Core Tools that are run via the `dotnet` command that collect telemetry.

`dotnet` 命令是用于启动应用程序和 .NET Core 工具。`dotnet` 命令它本身不会收集遥测数据。它是 `dotnet` 命令通过运行 .NET Core 工具来收集遥测数据。

.NET Core commands (telemetry is not enabled):
.NET Core 命令（遥测未启用）：

- `dotnet`
- `dotnet [path-to-app]`

.NET Core Tools [commands](index.md) (telemetry is enabled), such as:
.NET Core 工具 [命令](index.md) （遥测启用），例如：

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

##Behavior
##行为

The .NET Core Tools telemetry feature is enabled by default. You can opt-out of the telemetry feature by setting an environment variable DOTNET_CLI_TELEMETRY_OPTOUT (for example, `export` on macOS/Linux, `set` on Windows) to true (for example, “true”, 1).

默认情况下 .NET Core 工具遥测功能是启用的。你可以选择退出遥感功能，通过设置一个环境变量 DOTNET_CLI_TELEMETRY_OPTOUT （例如：在 macOS/Linux 上的 `export`，在 Windows 上的 `set`）为 true （例如：“true”，1）。

##Data Points
##数据点

The feature collects the following pieces of data:
该功能收集以下几部分数据：

- The command being used (for example, “build”, “restore”)
- The ExitCode of the command
- For test projects, the test runner being used
- The timestamp of invocation
- The framework used
- Whether runtime IDs are present in the “runtimes” node
- The CLI version being used

- 正在使用的命令（例如： “build”、“restore”）
- 命令退出代码
- 对于测试项目，正在使用的测试器
- 调用的时间戳
- 使用的框架
- 运行时的 IDs 是否与当前 “runtimes” 节点一致
- 当前正在使用的 CLI 版本

The feature will not collect any personal data, such as usernames or emails. It will not scan your code and not extract any project-level data that can be considered sensitive, such as name, repo or author (if you set those in your project.json). We want to know how the tools are used, not what you are building with the tools. If you find sensitive data being collected, that’s a bug. Please [file an issue](https://github.com/dotnet/cli/issues) and it will be fixed.

该功能不会收集任何个人数据，比如用户名或者电子邮件。它不扫描你的代码，不提取任何可以视为敏感语句的项目级别数据，例如名称，仓库地址，或者作者（如果你在你的 project.json 设置这些）。我们想知道工具如何被使用，而不是你使用工具生成什么。如果你发现敏感的数据被收集，这是一个错误。请 [提交一个 issue](https://github.com/dotnet/cli/issues)，它将会被修复。

##License
##许可协议

The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula). This includes the “DATA” section re-printed below, to enable telemetry.

微软 .NET Core 分配的许可协议是 [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula)。为了启动遥感，这个包括 “DATA” 部分重新输出在下面。

[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use this same license but do not enable telemetry (see [Scope](#scope) above).

[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) 使用这个相同的许可协议，但是未开启遥感（参考上面的 [适用范围](#scope)）。

```text
2.      DATA.  The software may collect information about you and your use of
the software, and send that to Microsoft. Microsoft may use this information
to improve our products and services. You can learn more about data collection
and use in the help documentation and the privacy statement at
http://go.microsoft.com/fwlink/?LinkId=528096 . Your use of the software
operates as your consent to these practices.
```

## Disclosure
## 说明

The .NET Core Tools display the following text when you first run one of the commands (for example, `dotnet restore`). This "first run" experience is how Microsoft notifies you about data collection. This same experience also initially populates your NuGet cache with the libraries in the .NET Core SDK, avoiding requests to NuGet.org (or other NuGet feed) for these libraries.

当你首次运行一个命令（例如：`dotnet restore`）时， .NET Core 工具显示下面的文字。这个“首次运行”体验是微软如何通知你关于数据收集。同样的体验是，最初填充你的 NuGet 缓存在 .NET Core SDK 中，避免去 NuGet.org（或者其它 NuGet 源）请求这些库。

```text
Welcome to .NET Core!
---------------------

Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to
see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
---------

The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include commandline arguments. The data is
collected by Microsoft and shared with the community.

You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT
environment variable to 1 using your favorite shell.

You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-
telemetry.

Configuring...
--------------

A command is running to initially populate your local package cache, to
improve restore speed and enable offline access. This command will take up to
a minute to complete and will only happen once. 
```
