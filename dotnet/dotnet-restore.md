---
title: dotnet-restore
description: dotnet-restore
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 60489b25-38de-47e6-bed1-59d9f42e2d46
---

dotnet-restore
==============

## NAME
## 名称

`dotnet-restore` - Restores the dependencies and tools of a project

`dotnet-restore` - 还原一个项目的依赖项和工具

## SYNOPSIS
## 概要

`dotnet restore [--source]  
    [--packages] [--disable-parallel]  
    [--fallbacksource] [--configfile] [--verbosity]
    [<root>]`  

## DESCRIPTION
## 描述

The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project.json file. 
By default, the restoration of dependencies and tools are done in parallel.

`dotnet restore` 命令使用 NuGet 还原在 project.json 文件中被指定的依赖项，以及项目特定工具。
默认情况下，依赖项和工具的恢复是并行完成的。

In order to restore the dependencies, NuGet needs the feeds where the packages are located. 
Feeds are usually provided via the NuGet.config configuration file; a default one is present when the CLI tools are installed. 
You can specify more feeds by creating your own NuGet.config file in the project directory. 
Feeds can also be specified per invocation on the command line. 

为了还原依赖项，需要提供 NeGet 包所在位置的源。
源通常是通过 NuGet.config 配置文件提供的；安装了 CLI 工具时默认存在一个。
你可以通过在项目目录中创建自己的 NuGet.config 文件指定更多的源。
源也可以在每次调用命令行上指定。

For dependencies, you can specify where the restored packages are placed during the restore operation using the 
`--packages` argument. 
If not specified, the default NuGet package cache is used. 
It is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, `/home/user1` on Linux or `C:\Users\user1` on Windows).

对于依赖项，你可以在还原操作时使用 `--packages` 参数指定还原包的位置。
如果没有指定，默认使用 NuGet 包缓存。
它存在所有的操作系统上的用户目录下的 `.nuget/packages` 目录中（例如，Linux 上的 `/home/user1` 或者是 Windows 上的 `C:\Users\user1`）。

For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then
proceeds to restore the tool's dependencies as specified in its project.json. 

对于项目特定的工具，`dotnet restore` 首先还原该工具打包的包，然后继续还原在 project.json 中指定的工具依赖项。

## OPTIONS
## 选项

`[root]` 
    
 A list of projects or project folders to restore. The list can contain either a path to a `project.json` file, or a path to `global.json` file or folder. The restore operation runs recursively for all subdirectories and restores for each given project.json file it finds.

 还原的项目或者项目目录的列表。该列表可以是包含一个 `project.json` 文件的路径，或者一个 `global.json` 文件或文件夹的路径中的一个。还原操作递归运行所有子目录，并还原找到的每个给定的 project.json 文件。

`-s`, `--source` [SOURCE]

Specifies a source to use during the restore operation. This overrides all of the sources specified in the NuGet.config file(s). Multiple sources can be provided by specifying this option multiple times.

指定一个在还原操作期间使用的源。这覆盖所有在 NuGet.config 文件中指定的源。多个源可以通过指定此选项多次来提供。

`--packages` [DIR]

Specifies the directory to place the restored packages in. 

指定要放置还原的包的目录。

`--disable-parallel`

Disables restoring multiple projects in parallel. 

禁用并还原多个项目。

`-f`, `--fallbacksource` [FEED]

Specifies a fallback source that will be used in the restore operation if all other sources fail. All valid feed formats are allowed. Multiple fallback sources can be provided by specifying this option multiple times.

`--configfile` [FILE]

Configuration file (NuGet.config) to use for the restore operation. 

用于还原操作的配置文件（NuGet.config）。

`--verbosity` [LEVEL]

The verbosity of logging to use. Allowed values: Debug, Verbose, Information, Minimal, Warning, or Error.

使用日志详细级别。允许的值：Debug、 Verbose、 Information、Minimal、Warning 或者 Error。

## EXAMPLES
## 例子

`dotnet restore`

Restores dependencies and tools for the project in the current directory. 

还原在当前目录中的项目的依赖项和工具。

`dotnet restore ~/projects/app1/project.json`
    
Restores dependencies and tools for the `app1` project found in the given path.

还原在给定的路径发现 `app1` 项目依赖项和工具。
	
`dotnet restore -f c:\packages\mypackages`
    
Restores the dependencies and tools for the project in the current directory using the file path provided as the fallback source. 

还原在当前目录中的项目的依赖项和工具，使用文件路径作为备用源。

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages`
	
Restores the dependencies and tools for the project in the current directory using the two file paths provided as the fallback sources. 

还原在当前目录中的项目的依赖项和工具，使用两个文件路径作为备用源。

`dotnet restore --verbosity Error`
    
Restores dependencies and tools for the project in the current directory and shows only errors in the output.

还原在当前目录中的项目的依赖项和工具，并在输出中仅显示 errors。
