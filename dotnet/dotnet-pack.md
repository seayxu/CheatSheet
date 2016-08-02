---
title: dotnet-pack
description: dotnet-pack
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8b4b8cef-f56c-4a10-aa01-fde8bfaae53e
---

dotnet-pack
===========

## NAME
## 名称

`dotnet-pack` - Packs the code into a NuGet package

`dotnet-pack` - 将代码打包成 NuGet 包

## SYNOPSIS
## 概要

`dotnet pack [--output]  
    [--no-build] [--build-base-path]  
    [--configuration]  [--version-suffix]
    [<project>]`  

## DESCRIPTION
## 描述

The `dotnet pack` command builds the project and creates NuGet packages. The result of this operation is two packages with the `nupkg` extension. One package contains the code and the other contains the debug symbols. 

`dotnet pack` 命令生成项目并创建 NuGet 包。这个操作的结果是两个 `nupkg` 扩展名的包。一个包含代码，另一个包含调试符号。

NuGet dependencies of the project being packed are added to the nuspec file, so they are able to be resolved when the package is installed. 
Project-to-project references are not packaged inside the project by default. If you wish to do this, you need to reference the required project in your dependencies node with a `type` set to "build" like in the following example:

该项目被依赖的 NuGet 包装被添加到 nuspec 文件，因此，他们能够在安装包时得到解决。
默认情况下，项目到项目之间的引用是不打包到项目中的。如果你想那样做，你需要在你的依赖中引用需要项目的 `type` 节点设置为 “build” ，设置就像下面的例子：

```json
{
    "version": "1.0.0-*",
    "dependencies": {
        "ProjectA": {
            "target": "project",
            "type": "build"
        }
    }
}
```

`dotnet pack` by default first builds the project. If you wish to avoid this, pass the `--no-build` option. This can be useful in Continuous Integration (CI) build scenarios in which you know the code was just previously built, for example. 

默认情况下，`dotnet pack` 首先生成项目。如果你想避免这样，传递 `--no-build` 选项。这在持续集成（CI）构建场景，正如你知道代码仅仅是预生成的示例，会是有用的。

## OPTIONS
## 选项

`[project]` 
    
The project to pack. It can be either a path to a `project.json` file or to a directory. If omitted, it will
default to the current directory. 

打包的项目。它还可以是一个 `project.json` 文件的路径或者是目录。如果忽略，它将默认为当前目录。

`-o`, `--output` [DIR]

Places the built packages in the directory specified. 

指定生成的目录。

`--no-build`

Skips the building phase of the packing process. 

打包进程中跳过生成阶段。

`--build-base-path`

Places the temporary build artifacts in the specified directory. By default, they go to the obj directory in the current directory. 

指定临时生成产物的目录。默认情况下，它们在当前目录的 obj 目录。

`-c`, `--configuration [Debug|Release]`

Configuration to use when building the project. If not specified, will default to "Debug".

当生成项目时使用的配置。如果没有指定，将默认为 “Debug”。

## EXAMPLES
## 例子

`dotnet pack`

Packs the current project.

打包当前项目。

`dotnet pack ~/projects/app1/project.json`
    
Packs the app1 project.

打包 app1 项目。
	
`dotnet pack --output nupkgs`
    
Packs the current application and place the resulting packages into the specified folder.

打包当前的应用程序，并将生成的包放置到指定的文件夹中。

`dotnet pack --no-build --output nupkgs`

Packs the current project into the specified folder and skips the build step.

打包当前的项目到指定的文件夹中，并跳过生成步骤。
