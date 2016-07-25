---
title: .NET Core Command Line Tools (CLI)
description: .NET Core Command Line Tools (CLI)
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b70e9ac0-c8be-49f7-9332-95ab93e0e7bc
---

# .NET Core Command Line Tools
# .NET Core 命令行工具

## What is the .NET Core Command Line Interface (CLI)?
## 什么是 .NET Core 命令行界面（CLI）？
The .NET Core CLI is a new foundational cross-platform toolchain for developing 
.NET Core applications. It is "foundational" because it is the primary layer on which other, 
higher-level tools, such as Integrated Development Environments (IDEs), editors and 
build orchestrators can build on. 

.NET Core CLI 是为开发 .NET Core 应用程序的一个新的跨平台工具链基础。它是“基础”，因为它是在其它的，高级别工具的主要层，如集成开发环境（IDEs），由编辑器和构建者组成。

It is also cross-platform by default and has the same surface area on each of the supported platforms. This means that
when you learn how to use the tooling, you can use it the same way from any of the supported platforms. 

它默认也是跨平台的，并且对每个支持的平台有相同的表现范围。这意味着，当你学会如何使用工具，你可以从任何支持的平台上以同样的方式使用它。

## Installation
## 安装
As with any tooling, the first thing is to get the tools to your machine. Depending on your scenario, you can either 
use the native installers to install the CLI or use the installation shell script.

和任何工具一样，第一件事就是获取工具到你的机器上。根据你的情况，你可以使用本地安装程序安装 CLI 或使用安装脚本。

The native installers are primarily meant for developer's machines. The CLI is distributed using each supported platform's 
native install mechanism, for instance DEB packages on Ubuntu or MSI bundles on Windows. These installers will install 
and set up the environment as needed for the user to use the CLI immediately after the install. However, they also 
require administrative privileges on the machine. You can view the installation instructions on the
[.NET Core getting started page](https://aka.ms/dotnetcoregs).

本地安装程序主要是用于开发的机器。CLI 是分别使用每个支持的平台的原生安装机制，例如在 Ubuntu 上的 DEB 包，或者在 Windows 上的 MSI 包。这些安装程序将安装和安装后用户立即使用 CLI 的需要设置环境。然而，在机器上它们也需要的管理特权。你可以在 [.NET Core 开始页](https://aka.ms/dotnetcoregs) 查看安装说明。

Install scripts, on the other hand, do not require administrative privileges. However, they will also not install any 
prerequisites on the machine; you need to install all of the prerequisites manually. The scripts are meant mostly for 
setting up build servers or when you wish to install the tools without administrative privileges (do note the prerequisites 
caveat above). You can find more information on the [install script reference topic](dotnet-install-script.md). If you are 
interested in how to set up CLI on your continuous integration (CI) build server you can take a look at the 
[CLI with CI servers](using-ci-with-cli.md) document. 

安装脚本，另一方面，不需要管理权限。然而，它们将也不安装任何必备的事物在机器上；你需要手动安装所有的必备的事物。脚本是用于安装建立服务器或当你没有管理特权时希望安装工具（请注意上面提示的必备的事物）。你可以在 [安装脚本参考主题](dotnet-install-script.md) 找到更多的信息。如果你对如何在持续集成（CI）生成服务器上配置 CLI，请查看 [CLI 和 CI 服务器](using-ci-with-cli.md) 文档。

By default, the CLI will install in a side-by-side (SxS) manner. This means that multiple versions of the CLI tools 
can coexist at any given time on a single machine. How the correct version gets used is explained in more detail in 
the [driver section](#driver) below. 

默认情况下，CLI 将以一个并行的（SxS）方式安装。这意味着的多个版本的 CLI 工具可以在一台机器上在任何给定的时间共存。如何正确的解释得到使用是在下面的 [驱动部分](#driver) 中更详细的说明。

### What commands come in the box?
### 盒子出现什么命令？
The following commands are installed by default:
默认情况下安装以下命令：

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [run](dotnet-run.md)
* [build](dotnet-build.md)
* [test](dotnet-test.md)
* [publish](dotnet-publish.md)
* [pack](dotnet-pack.md)

There is also a way to import more commands on a per-project basis as well as to add your own commands. This is 
explained in greater detail in the [extensibility section](#extensibility). 

也有一种方法可以在每个项目基础上导入更多的命令，以及添加自己的命令。这是更详细的说明在 [可扩展性部分](#extensibility)。

## Working with the CLI
## 使用 CLI 工作

### A short sample
### 一个简短的例子
Before we go into any more details, let's see how working with the CLI looks like from a 10,000-foot view. 
The sample below utilizes several commands from the CLI standard install to initialize a new simple console application, 
restore the dependencies, build the application and then run it. 

在我们进入任何更多细节之前，让我们看看如何使用 CLI 工作，看起来像来自 10,000 英寸的视图。
下面的示例使用来自正常安装的 CLI 几个命令，初始化一个新的、简单的控制台应用程序，还原依赖项，生成应用程序并运行它。

```console
dotnet new
dotnet restore
dotnet build --output /stuff
dotnet /stuff/new.dll
```

### How does it work?
### 它如何工作？
As we saw in the short sample [above](#a-short-sample), there is a pattern in the way you use the CLI tools. Within that pattern, we can 
identify three main pieces of each command:

正如 [上面](#a-short-sample) 看到的简短的示例，当你使用 CLI 工具有一个模式。在这个模式中，我们可以识别每个命令的三个主要部分：

1. The driver ("dotnet")
2. The command, or "verb"
3. Command arguments

1. 驱动程序（“dotnet”）
2. 命令或者 “verb”
3. 命令参数

Let's dig into more details on each of the above.

让我们深入到上面每个的更多细节。

### Driver
### 驱动程序
The driver is named `dotnet`. It is the first part of what you invoke. The driver has two responsibilities:

驱动程序被命名为 `dotnet`。它是你调用的第一部分。这个驱动程序有两个功能：

1. Executing IL code
2. Executing the verb

1. 执行 IL 代码
2. 执行动词（verb）

Which of the two things it does is dependent on what is specified on the command line. In the first case, you would 
specify an IL assembly that `dotnet` would run similar to this: `dotnet /path/to/your.dll`. 

它所做的两件事依赖于在命令行上指定的东西。在第一种情况下，你可以指定一个 IL 程序集，`dotnet` 运行类似这个：`dotnet /path/to/your.dll`。

In the second case, the driver attempts to invoke the specified command. This will start the CLI command execution 
process. First, the driver will determine the version of the tooling that you want. You can specify the version in the 
`global.json` file using the `sdkVersion` property. If that is not available, the driver will find the latest version
of the tools that is installed on disk and will use that version. Once the version is determined, it will execute the 
command. 

在第二种情况下，该驱动程序试图调用指定的命令。这将开启 CLI 命令执行进程。首选，该驱动程序将确定你想要的工具的版本。你可以在 `global.json` 文件中使用 `sdkVersion` 属性指定版本。如果那个不可用，该驱动程序将查找已经在磁盘上安装的工具的最新版本并将使用该版本。一旦版本被确定，它将执行命令。

### The "verb"
### “动词”
The verb is simply a command that performs an action. `dotnet build` will build your code. `dotnet publish` will publish 
your code. The verb is implemented as a console application that is named per convention: `dotnet-{verb}`. All of the 
logic is implemented in the console application that represents the verb. 

动词是简单的执行操作命令。`dotnet build` 将生成代码。`dotnet publish` 将发布代码。动词被实现是作为一个按每一个约定命名的控制台应用程序：`dotnet-{verb}`。所有的逻辑是表示动词的控制台应用程序实现的。

### The arguments
### 参数
The arguments that you pass on the command line are the arguments to the actual verb/command being invoked. 
For example, when you type `dotnet publish --output publishedapp` the `--output` argument is passed to the 
`publish` command. 

在命令行上传递的参数是实际调用的 verb/command 的参数。
例如，当你键入 `dotnet publish --output publishedapp`，`--output` 参数被传递给 `publish` 命令。

## Types of application portability
## 可移植应用程序的类型
CLI enables applications to be portable in two main ways:

CLI 使应用程序可以移植在两个主要方面：

1. Completely portable application that can run anywhere .NET Core is installed
2. Self-contained applications

1. 完全可移植的应用可以在任何安装 .NET Core 地方运行
2. 独立的应用程序

You can learn more about both of these in the [application types overview](../app-types.md) topic. 

你可以在 [应用程序类型描述](../app-types.md) 主题了解更多有关这两种。

## Migration from DNX
## 从 DNX 迁移
If you used DNX in RC1 of .NET Core, you may be wondering what happened to it and how do these new tools
relate to the DNX tools. In short, the DNX tools have been replaced with the .NET Core CLI tools. 
If you have existing projects or are just wondering how the commands map, you
can use the [DNX to CLI migration document](../migrating-from-dnx.md) to get all of the details. 

如果你使用 .NET Core RC1 DNX，你可能想知道发生了什么和这些新工具与 DNX 工具如何有联系。总而言之，DNX 工具已经被 .NET Core CLI 工具代替了。
如果你有已存在的项目，或者是仅仅想知道命令如何映射，你可以使用 [DNX 迁移到 CLI 文档](../migrating-from-dnx.md) 来获取所有的详细信息。

## Extensibility
## 扩展性
Of course, not every tool that you could use in your workflow will be a part of the core CLI tools. However, .NET Core 
CLI has an extensibility model that allows you to specify additional tools for your projects. You can find out more 
in the [可扩展性文档](extensibility.md). 

当然，不是每一个工具你可以使用你的工作将是 core CLI 工具的一部分。但是，.NET Core CLI 具有扩展模式，允许你为你的项目指定额外的工具。你可以在 [extensibility document](extensibility.md) 查出更多信息。

## More resources
## 更多资源
This was a short overview of the most important features of the CLI. You can find out more by using the reference and 
conceptual topics on this site. There are also other resources you can use:

这是 CLI 的最重要的一个特征的简短概述。在这个网站你可以找到更多的使用参考和概念主题。也有其他的资源你可以使用：

* [GitHub repo](https://github.com/dotnet/cli/)
* [Getting Started instructions](https://aka.ms/dotnetcoregs/)

