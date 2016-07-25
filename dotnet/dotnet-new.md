---
title: dotnet-new
description: dotnet-new
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 263c3d05-3a47-46a6-8023-3ca16b488410
---

dotnet-new
==========

## NAME
## 名称
dotnet-new -- Creates a new .NET Core project

dotnet-new -- 创建一个新的 .NET Core 项目

## SYNOPSIS
## 概要
`dotnet new [--type] [--lang]`

## DESCRIPTION
## 描述
The `dotnet new` command provides a convenient way to initialize a valid .NET Core project and sample source code to try out the Command Line Interface (CLI) toolset. 

`dotnet new` 命令提供了一个便捷的方法来初始化一个有效的 .NET Core 项目和示例源代码，用来试验命令行界面（CLI）工具集。

This command is invoked in the context of a directory. When invoked, the command will result in two main artifacts being dropped to the directory: 

这个命令在目录的上下文中被调用。当调用时，该命令将导致两个主要的部件被放到到目录中：

1. A `Program.cs` (or `Program.fs`) file that contains a sample "Hello World" program.
2. A valid `project.json` file.

1. 一个 `Program.cs` （或者 `Program.fs`）文件，包含一个“Hello World”示例程序。
2. 一个有效的 `project.json` 文件。

After this, the project is ready to be compiled and/or edited further. 

在此之后，该项目已准备好被编译和（或者）进一步编辑。

## Options
## 选项

`-l`, `--lang [C#|F#]`

Language of the project. Defaults to `C#`. `csharp` (`fsharp`) or `cs` (`fs`) are also valid options.

项目的语言。默认是 `C#`。`csharp`（`fsharp`）或者 `cs`（`fs`）同样是有效的选项。

`-t`, `--type`

Type of the project. Valid values are `console`, `web`, `lib` and `xunittest`. 

项目类型。有效的值是 `console`，`web`，`lib` 和 `xunittest`。

## EXAMPLES
## 例子

`dotnet new`
    
Drops a C# project in the current directory.

在当前目录放一个 C# 项目。

`dotnet new --lang f#`
    
Drops an F# project in the current directory.

在当前目录中放一个 F# 项目。

`dotnet new --lang c#`
    
Drops an C# project in the current directory.

在当前目录放一个 C# 项目。

`dotnet new -t web`
    
Drops a new ASP.NET Core project in the current directory. 

在当前目录放一个新的 ASP.NET Core 项目。
