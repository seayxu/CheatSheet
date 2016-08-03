---
title: dotnet-publish
description: dotnet-publish
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
---

dotnet-publish
==============

## NAME
## 名称

`dotnet-publish` - Packs the application and all of its dependencies into a folder getting it ready for publishing

`dotnet-publish` - 打包应用程序及其所有依赖到一个文件夹中，获取后准备发布

## SYNOPSIS
## 概要

`dotnet publish [--framework]  
    [--runtime] [--build-base-path] [--output]  
    [--version-suffix] [--configuration]  
    [<project>]`  

## DESCRIPTION
## 描述

`dotnet publish` compiles the application, reads through its dependencies specified in the `project.json` file and publishes the resulting set of files to a directory. 

`dotnet publish` 编译应用程序，通过读取在 project.json 文件中指定的依赖，并发布结果集的文件到一个目录。

Depending on the type of portable app, the resulting directory will contain the following:

根据便携式应用的类型，所得到的目录将包含以下内容：

1. **Portable application** - application's intermediate language (IL) code and all of application's managed dependencies.
    * **Portable application with native dependencies** - same as above with a sub-directory for the supported platform of each native
    dependency. 
2. **Self-contained application** - same as above plus the entire runtime for the targeted platform.

1. **便携式应用程序** - 应用程序的中间语言（IL）代码和所有应用程序的关联依赖。
    * **本地的依赖的便携式应用** - 与上面的子目录的每个本地依赖支持的平台。
2. **自包含应用程序** - 与上述相同，并附加用于目标平台的整个运行时。

The above types are covered in more details in the [types of portable applications](../app-types.md) topic.

上面的类型涵盖更多细节在 [types of portable applications](../app-types.md) 主题。

## OPTIONS
## 选项

`[project]` 
    
`dotnet publish` needs access to the `project.json` file to work. If it is not specified on invocation via [project], `project.json` in the current directory will be the default.     
If no `project.json` can be found, `dotnet publish` will throw an error. 

`dotnet publish` 工作需要访问 `project.json` 文件。如果它没有通过指定的 [project] 调用，当前目录中的 `project.json` 将为默认值。
如果没有 `project.json` 可以被发现，`dotnet publish` 将抛出一个错误。

`-f`, `--framework` [FID]

Publishes the application for a given framework identifier (FID). If not specified, FID is read from `project.json`. In no valid framework is found, the command will throw an error. If multiple valid frameworks are found, the command will publish for all valid frameworks. 

发布给定框架标识（FID）应用程序。如果没有指定，FID 从 `project.json` 中读取。发现没有有效的框架时，命令将抛出一个错误。如果发现多个有效的框架，命令将发布所有有效的框架。

`-r`, `--runtime` [RID]

Publishes the application for a given runtime. 

发布给定运行时应用程序。

`-b`, `--build-base-path` [DIR]

Directory in which to place temporary outputs.

临时输出的目录。

`-o`, `--output`

Specify the path where to place the directory. If not specified, it will default to _./bin/[configuration]/[framework]/_ 
for portable applications or _./bin/[configuration]/[framework]/[runtime]_ for self-contained applications.

指定在哪里放置目录的路径。如果没有指定，它将默认便携式应用程序为 _./bin/[configuration]/[framework]/_ 或者 自包含应用程序为 _./bin/[configuration]/[framework]/[runtime]_ 。

--version-suffix [VERSION_SUFFIX]

Defines what `*` should be replaced with in the version field in the project.json file.

定义在 project.json 文件中的版本字段什么 `*` 被替换。

`-c`, `--configuration [Debug|Release]`

Configuration to use when publishing. The default value is Debug.

发布时的配置。默认值是 Debug。

## EXAMPLES
## 例子

`dotnet publish`

Publishes an application using the framework found in `project.json`. If `project.json` contains `runtimes` node, publish for the RID of the current platform.

使用在 `project.json` 中发现的框架发布一个应用程序。如果 `project.json` 包含 `runtimes` 节点，发布 RID 为当前平台。

`dotnet publish ~/projects/app1/project.json`
    
Publishes the application using the specified `project.json`.

使用指定的 `project.json` 发布应用程序。

`dotnet publish --framework netcoreapp1.0`
    
Publishes the current application using the `netcoreapp1.0` framework.

使用 `netcoreapp1.0` 框架发布当前应用程序。
	
`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`
    
Publishes the current application using the `netcoreapp1.0` framework and runtime for `OS X 10.10`. This RID has to 
exist in the `project.json` `runtimes` node.

使用 `netcoreapp1.0` 框架和 `OS X 10.10` 运行时发布当前应用程序。这个 RID 必须存在于 `project.json` 中的 `runtimes` 节点。 
