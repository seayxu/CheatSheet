---
title: dotnet 命令
description: dotnet command
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 07/23/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 93015521-2127-4fe9-8fce-ca79bcc4ff49
---

dotnet command
==============
dotnet 命令
==============

## NAME
## 名称

dotnet -- General driver for running the command-line commands
dotnet -- 运行命令行命令的一般驱动程序

## SYNOPSIS
## 概要

`dotnet [--version] [--help] [--verbose] [--info] <command> [<args>]`

## DESCRIPTION
## 描述
`dotnet` 是命令行界面（CLI）工具链的通用驱动程序。调用它自己，会给出简短的使用说明。

Each specific feature is implemented as a command. In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md). All of the arguments following the command are its own arguments. 

每个特定的功能实现为一个命令。为了使用该功能，命令被指定在 `dotnet` 之后，例如 [`dotnet build`](dotnet-build.md)。所有跟在命令后面的参数都是自己的观点。

The only time `dotnet` is used as a command on its own is to run portable apps. Just specify a portable application DLL after the `dotnet` verb to execute the application.    

`dotnet` 作为自己唯一的一个命令是为了运行便携式的应用。仅指定一个便携式应用 DLL 在` dotnet ` 动词之后来执行应用程序。

## OPTIONS
## 选项
`-v, --verbose`

Enables verbose output.

可以详细的输出。

`--version`

Prints out the version of the CLI tooling.

打印出来 CLI 工具版本。

`--info`

Prints out more detailed information about the CLI tooling, such as the current operating system, commit SHA for the version, etc. 

打印出关于 CLI 工具更详细的信息，例如当前的操作系统，提交版本的 SHA，等等。

`-h, --help`

Prints out a short help and a list of current commands. 

打印出一个简短的帮助和当前命令列表。

## DOTNET COMMANDS
## DOTNET 命令

The following commands exist for dotnet:

* [dotnet-new](dotnet-new.md)
   * Initializes a C# or F# console application project.
* [dotnet-restore](dotnet-restore.md)
  * Restores the dependencies for a given application. 
* [dotnet-build](dotnet-build.md)
  * Builds a .NET Core application.
* [dotnet-publish](dotnet-publish.md)
   * Publishes a .NET portable or self-contained application.
* [dotnet-run](dotnet-run.md)
   * Runs the application from source.
* [dotnet-test](dotnet-test.md)
   * Runs tests using a test runner specified in the project.json.
* [dotnet-pack](dotnet-pack.md)
   * Creates a NuGet package of your code.


dotnet 存在以下命令:

* [dotnet-new](dotnet-new.md)
   * 初始化一个 C# 或者 F# 控制台应用程序。
* [dotnet-restore](dotnet-restore.md)
  * 还原一个给定应用程序的依赖。 
* [dotnet-build](dotnet-build.md)
  * 生成一个 .NET Core 应用。
* [dotnet-publish](dotnet-publish.md)
   * 发布一个便携式或者独立的 .NET 应用程序。
* [dotnet-run](dotnet-run.md)
   * 从源码运行应用程序。
* [dotnet-test](dotnet-test.md)
   * 使用在 project.json 中指定的一个测试机运行测试。
* [dotnet-pack](dotnet-pack.md)
   * 创建一个你的代码的 NuGet 包。

## EXAMPLES
## 例子

`dotnet new`

Initializes a sample .NET Core console application that can be compiled and run.

初始化一个可以被编译和运行的 .NET Core 示例控制台应用程序。

`dotnet restore`

Restores dependencies for a given application. 

还原一个给定应用的依赖。

`dotnet compile`

Compiles the application in a given directory. 

编译在给定目录的应用程序。

`dotnet myapp.dll`

Runs a portable app named `myapp.dll`. 

运行一个名为 `myapp.dll` 的便携式应用程序。

## ENVIRONMENT 
## 环境变量 

`DOTNET_PACKAGES`

The primary package cache. If not set, it defaults to $HOME/.nuget/packages on Unix or %HOME%\NuGet\Packages on Windows.

主要的包缓存。如果没有设置，它默认在 Unix 上是 $HOME/.nuget/packages，或者在 Windows 上是 %HOME%\NuGet\Packages。

`DOTNET_SERVICING`

Specifies the location of the servicing index to use by the shared host when loading the runtime.

指定被用于共享宿主在加载运行时的服务索引的位置。

`DOTNET_CLI_TELEMETRY_OPTOUT`

Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft. **true** to opt-out of the telemetry feature (values true, 1 or yes accepted); otherwise, **false** (values false, 0 or no accepted). If not set, it defaults to **false**, that is, the telemetry feature is on.

指定有关 .NET Core 工具的使用数据是否被收集并发送到 Microsoft。**true** 选择出的遥测功能（值为 true，1 或 yes 可接受）；否则，**false** （值为 false， 0 或者 no 可接受）。如果没有设置，默认是 **false**，以至于，遥测功能是开启的。