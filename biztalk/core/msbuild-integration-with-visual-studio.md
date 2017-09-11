---
title: "MSBUILD Integration with Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aedcabf7-b2cf-482a-9ade-7311e104bff9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBUILD Integration with Visual Studio
Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects. Project settings added and changed through Visual Studio are reflected in the .btproj file that is generated for each project. Visual Studio uses a hosted instance of MSBUILD to build BizTalk projects, meaning that a BizTalk project can be built in Visual Studio or from the command line, with identical results.  
  
 For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).  
  
 The following procedure shows you how to use MSBUILD to build a sample BizTalk project from command line.  
  
## To build a BizTalk project from a command line  
  
1.  Start **Visual Studio Command Prompt**.  
  
2.  Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!NOTE]
    >  The solution may contain BizTalk and non-BizTalk projects, such as a C# class library.