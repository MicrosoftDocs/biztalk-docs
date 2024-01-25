---
description: "Learn more about: MSBUILD Integration with Visual Studio"
title: "MSBUILD Integration with Visual Studio"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MSBUILD Integration with Visual Studio
Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects. Project settings added and changed through Visual Studio are reflected in the .btproj file that is generated for each project. Visual Studio uses a hosted instance of MSBUILD to build BizTalk projects, meaning that a BizTalk project can be built in Visual Studio or from the command line, with identical results.

 For more information on MSBUILD, see [https://go.microsoft.com/fwlink/?LinkId=193567](/previous-versions/visualstudio/visual-studio-2015/msbuild/msbuild).

 The following procedure shows you how to use MSBUILD to build a sample BizTalk project from command line.

## To build a BizTalk project from a command line

1.  Start **Visual Studio Command Prompt**.

2.  Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.

    ```
    msbuild unittesttest.sln /p:Configuration=Debug
    ```

    > [!NOTE]
    >  The solution may contain BizTalk and non-BizTalk projects, such as a C# class library.