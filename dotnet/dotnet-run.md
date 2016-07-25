---
title: dotnet-run
description: dotnet-run
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 495ff50b-cb30-4d30-8f20-beb3d5e7c31f
---

dotnet-run
==========

## NAME 
## 名称 

dotnet-run -- Runs source code 'in-place' without any explicit compile or launch commands.
dotnet-run -- Runs source code 'in-place' without any explicit compile or launch commands.

## SYNOPSIS
## 概要

`dotnet run [--framework] [--configuration]
    [--project] [--help] [--]`

## DESCRIPTION
## 描述
The `dotnet run` command provides a convenient option to run your application from the source code with one command. 
It compiles source code, generates an output program and then runs that program. 
This command is useful for fast iterative development and can also be used to run a source-distributed program (for example, a website).

`dotnet run` 命令提供了一个方便的选项使用一个命令从源代码来运行你的应用程序。
它编译源码，生成一个输出程序，然后运行那个程序。
这个命令对于快速迭代发展是有用的，也可以用于运行一个源码分布式程序（例如，网站）。

This command relies on [`dotnet build`](dotnet-build.md) to build source inputs to a .NET assembly, before launching the program. 
The requirements for this command and the handling of source inputs are all inherited from the build command. 
The documentation for the build command provides more information on those requirements.

这个命令依赖 [`dotnet build`](dotnet-build.md) 将源代码生成输入到 .NET 程序集，之后运行该程序。
这个命令和处理输入的源码的要求，都是继承自生成命令。

Output files are written to the child `bin` folder, which will be created if it doesn't exist. 
Files will be overwritten as needed. 
Temporary files are written to the child `obj` folder.  

输出的文件被写到 `bin` 子文件夹，如果它不存在则创建它。
根据需要，文件将被覆盖。
临时文件被写入到 `obj` 子文件夹。

In case of a project with multiple specified frameworks, `dotnet run` will first select the .NET Core frameworks. If those do not exist, it will error out. To specify other frameworks, use the `--framework` argument.

在一个具有多个特定框架的项目情况下，`dotnet run` 将首先选择 .NET Core 框架。如果这些不存在，将会输出错误。指定其他框架，使用 `--framework` 参数。

The `dotnet run` command must be used in the context of projects, not built assemblies. If you're trying to execute a DLL instead, you should use [`dotnet`](dotnet.md) without any command like in the following example:

`dotnet run` 命令必须在项目上下文中使用，不生成程序集。如果你想执行一个 DLL 作为替换，你应该使用不带任何参数的 [`dotnet`](dotnet.md) 命令，就像下面的例子：

`dotnet myapp.dll`

For more information about the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.

有关 `dotnet` 驱动的更多信息，查看 [.NET Core Command Line Tools (CLI)](index.md) 主题。

## OPTIONS
## 选项

`--`

Delimits arguments to `dotnet run` from arguments for the application being run. 
All arguments after this one will be passed to the application being run. 

从正在运行的应用程序的参数分离 `dotnet run` 参数。
这个命令之后的所有参数将被传递给正在运行的应用程序。

`-f`, `--framework` [FID]

Runs the application for a given framework identifier (FID). 

运行一个给定框架标识符（FID）的应用程序。

`-c`, `--configuration [Debug|Release]`

Configuration to use when publishing. The default value is "Debug".

发布时使用的配置。默认值是“Debug”。

`-p`, `--project [PATH]`

Specifies which project to run. 
It can be a path to a project.json file or to a directory containing a project.json file. It defaults to
current directory if not specified. 

指定运行的项目。
它可以是一个 project.json 文件的路径，或者是一个包含 project.json 文件的目录。如果没有指定，它默认是当前目录。

## EXAMPLES
## 例子

`dotnet run`

Runs the project in the current directory. 

`dotnet run --project /projects/proj1/project.json`

Runs the project specified.

`dotnet run --configuration Release -- --help`

Runs the project in the current directory. The `--help` argument above is passed to the application being run, since the `--` argument was used.
