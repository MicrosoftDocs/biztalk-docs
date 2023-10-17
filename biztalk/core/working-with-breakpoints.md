---
description: "Learn more about: Working with Breakpoints"
title: "Working with Breakpoints | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Orchestration Debugger, breakpoints"
  - "Orchestration Debugger, suspended orchestrations"
  - "Orchestration Debugger, Message Flow view"
  - "Orchestration Debugger, service options"
  - "Message Flow view [Orchestration Debugger]"
ms.assetid: aad1a2b0-d705-49cd-85f7-b0ab2e473bcc
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working with Breakpoints
You can set breakpoints by attaching to a suspended orchestration, or by setting a breakpoint on a class.  
  
> [!NOTE]
>  When you undeploy an assembly, the database maintains the tracking options and breakpoint information for that assembly. If you subsequently deploy the same assembly again, the options and breakpoint information for that assembly are restored.  
  
### To attach to a suspended orchestration  
  
1.  Select an automatically suspended orchestration using a suspend shape, and then go to Step 3.  
  
2.  Refresh the view to check that the instance now appears in a Suspended state.  
  
3.  Click **Resume in Debug**.  
  
     The orchestration resumes in an In Breakpoint state. You can now debug interactively.  
  
### To switch to the Message Flow view  
  
-   Right-click a cell in the Results list and select **Message Flow** from the shortcut menu.  
  
## See Also  
 [Working with the Orchestration Debugger View](../core/working-with-the-orchestration-debugger-view.md)
