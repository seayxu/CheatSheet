---
title: dotnet-build
description: dotnet-build
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
---

dotnet-build
===========

## NAME 
## 名称 
dotnet-build -- Builds a project and all of its dependencies 

dotnet-build -- 生成项目和所有的依赖

## SYNOPSIS
## 概要

`dotnet build [--output]  
    [--build-base-path] [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`  

## DESCRIPTION
## 描述

The `dotnet build` command builds multiple source file from a source project and its dependencies into a binary. 
The binary will be in Intermediate Language (IL) by default and will have a DLL extension. 
`dotnet build` will also drop a `\*.deps` file which outlines what the host needs to run the application.  

`dotnet build` 命令从源项目中的多个源文件及其依赖成生成一个二进制文件。默认情况下，该二进制文件将在中间语言（IL）中，并且将有一个 DLL 扩展。`dotnet build` 也将生成一个宿主应用程序运行需要的 `\*.deps` 大纲文件。

Building requires the existence of a lock file, which means that you have to run [`dotnet restore`](dotnet-restore.md) prior to building your code.

生成需要存在一个锁定文件，这就是说你必须预先运行 [`dotnet restore`](dotnet-restore.md) 在生成你的代码之时。

Before any compilation begins, the build verb analyzes the project and its dependencies for incremental safety checks.
If all checks pass, then build proceeds with incremental compilation of the project and its dependencies; 
otherwise, it falls back to non-incremental compilation. Via a profile flag, users can choose to receive additional 
information on how they can improve their build times.

任何编译开始之前，生成动词分析项目及其增量安全检查的依赖。如果所有的检查都通过了，然后继续生成与项目及其依赖的增量编译；否则，它退到非渐进式编译。通过侧面的标志，用户可以选择接收他们如何能提高他们的生成时间的附加信息。

All projects in the dependency graph that need compilation must pass the following safety checks in order for the 
compilation process to be incremental:
- not use pre/post compile scripts
- not load compilation tools from PATH (for example, resgen, compilers)
- use only known compilers (csc, vbc, fsc)

依赖图中需要编译的所有项目必须通过下面的安全检查，以便编译过程是增量：
- 不要使用前/后编译脚本
- 没有从 PATH 加载编译工具（例如：resgen，编译器）
- 使用仅已知的编译器（CSC，VBC，FSC）

In order to build an executable application, you need a special configuration section in your project.json file:

为了生成一个可执行的应用程序，你需要在你的 project.json 文件中的特殊配置部分：

```json
{ 
    "compilerOptions": {
      "emitEntryPoint": true
    }
}
```

## OPTIONS
## 选项

`-o`, `--output` [DIR]

Directory in which to place the built binaries.

放置生成的二进制文件的目录。 

`-b`, `--build-base-path` [DIR]

Directory in which to place temporary outputs.

放置临时输出的目录。

`-f`, `--framework` [FRAMEWORK]

Compiles for a specific framework. The framework needs to be defined in the project.json file.

编译一个指定的框架。该框架需要在 project.json 文件中定义。

`-c`, `--configuration` [Debug|Release]

Defines a configuration under which to build.  If omitted, it defaults to Debug.

定义生成下的一个配置。如果省略，则默认为调试。

`-r`, `--runtime` [RUNTIME_IDENTIFIER]

Target runtime to build for. 

生成的目标运行时。

`--version-suffix` [VERSION_SUFFIX]

Defines what `*` should be replaced with in the version field in the project.json file. The format follows NuGet's version guidelines. 

定义了 `*` 应在 project.json 文件中的版本字段被更换。格式参照 NuGet 的版本风格。

`--build-profile`

Prints out the incremental safety checks that users need to address in order for incremental compilation to be automatically turned on.

打印出用户需要为了渐进式编译解决增量的安全检查自动打开。

`--no-incremental`

Marks the build as unsafe for incremental build. This turns off incremental compilation and forces a clean rebuild of the project dependency graph.

标志着构建为不安全的增量生成。这将关闭增量编译，迫使项目依赖关系图的干净重建。

`--no-dependencies`

Ignores project-to-project references and only builds the root project specified to build.

忽略项目到项目的引用，只有生成指定生成的根项目。