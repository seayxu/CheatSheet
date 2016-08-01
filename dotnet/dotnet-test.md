---
title: dotnet-test
description: dotnet-test
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
---

dotnet-test
================

## NAME
## 名称

`dotnet-test` - Runs unit tests using the configured test runner

`dotnet-test` - 使用配置的测试运行器运行单元测试

## SYNOPSIS
## 概要

`dotnet test [--configuration]  
    [--output] [--build-base-path] [--framework] [--runtime]
    [--no-build]
    [--parentProcessId] [--port]  
    [<project>]`  

## DESCRIPTION
## 描述

The `dotnet test` command is used to execute unit tests in a given project. Unit tests are class library 
projects that have dependencies on the unit test framework (for example, NUnit or xUnit) and the 
dotnet test runner for that unit testing framework. 
These are packaged as NuGet packages and are restored as ordinary dependencies for the project.

`dotnet test` 命令是用于在给定的项目执行单元测试。单元测试是依赖关系于单元测试框架（例如：NUnit 或 xUnit）的类库项目，并且该单元测试框架是用于 dotnet 测试运行器。

Test projects also need to specify a test runner property in project.json using the "testRunner" node. 
This value should contain the name of the unit test framework.

测试项目需要在 project.json 中使用“testRunner”节点指定一个的测试运行器属性。这个值应该包含单元测试框架的名称。

The following sample project.json shows the properties needed:

下面示例 project.json 展示需要的属性：

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {
    "System.Runtime.Serialization.Primitives": "4.1.1",
    "xunit": "2.1.0",
    "dotnet-test-xunit": "1.0.0-rc2-192208-24"
  },
  "testRunner": "xunit",
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.0.0"
        }
      },
      "imports": [
        "dotnet5.4",
        "portable-net451+win8"
      ]
    }
  }
}
```
`dotnet test` supports two running modes:

`dotnet test` 支持两种运行模式：

1. Console: In console mode, `dotnet test` simply executes fully any command gets passed to it and outputs the results. Anytime you invoke `dotnet test` without passing --port, it runs in console mode, which in turn will cause the runner to run in console mode.
2. Design time: used in the context of other tools, such as editors or Integrated Development Environments (IDEs). You can find out more about this mode in the [dotnet-test protocol](test-protocol.md) document. 

1. 控制台：在控制台模式下，`dotnet test` 是完全执行被传递给它的任意命令，并输出结果。任何时候你调用 `dotnet test` 没有传递 --port，它运行在控制台模式下，这反过来将导致运行器在控制台模式下运行。
2. 设计阶段：在其他工具，比如编辑器或集成开发环境（IDEs）的上下文中使用。你可以在 [dotnet-test protocol](test-protocol.md) 找到更多关于这个模式的文档。

## OPTIONS
## 选项

`[project]`
    
Specifies a path to the test project. If omitted, it defaults to current directory. 

指定要测试项目的路径。如果省略，则默认为当前目录。

`-c`, `--configuration` [Debug|Release]

Configuration under which to build. The default value is Release. 

用于生成下的配置。默认值是 Release。

`-o`, `--output` [DIR]

Directory in which to find binaries to run.

找到二进制运行的目录。

`-b`, `--build-base-path` [DIR]

Directory in which to place temporary outputs.

临时输出的目录。

`-f`, `--framework` [FRAMEWORK]

Looks for test binaries for a specific framework.

查看测试二进制文件的指定框架。

`-r`, `--runtime` [RUNTIME_IDENTIFIER]

Look for test binaries for a for the specified runtime.

查看测试二进制文件的指定运行时。

`--no-build` 

Does not build the test project prior to running it. 

没有生成之前，运行它的测试项目。

--parentProcessId

Used by IDEs to specify their process ID. Test will exit if the parent process does.

通过 IDEs（集成开发环境）指定进程的 ID。如果父进程已经处理了，测试将退出。

`--port`

Used by IDEs to specify a port number to listen for a connection.

通过 IDEs（集成开发环境）指定端口号来侦听连接。

## EXAMPLES
## 例子

`dotnet test`

Runs the tests in the project in the current directory. 

在当前目录中的项目运行测试。

`dotnet test /projects/test1/project.json`

Runs the tests in the test1 project. 

在 test1 项目中运行测试。

## SEE ALSO
## 参考

* [dotnet-test communication protocol](test-protocol.md)

* [dotnet-test通信协议](test-protocol.md)
