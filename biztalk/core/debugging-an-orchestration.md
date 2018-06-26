---
title: "Debugging an Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debugging, Orchestration Debugger"
  - "debugging, orchestrations"
  - "Orchestration Debugger, about Orchestration Debugger"
  - "Orchestrations Debugger"
  - "orchestrations, debugging"
  - "debugging, HAT"
  - "HAT, debugging"
ms.assetid: aae99cfd-d3dd-41c8-ae7a-b2733352cd69
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Debugging an Orchestration
The Orchestration Debugger enables you to track the activity of a single orchestration instance on a shape-by-shape basis. It displays a rendered view of the orchestration created in the Orchestration Designer.  
  
 You access the Orchestration Debugger in the Group Overview Page in the BizTalk Server Administration Console.  This is done from the output of a tracking query through a shortcut menu by right-clicking any service or message instance associated with an orchestration type. Once you're in i this page, you can switch back and forth between the Orchestration Debugger and the Message Flow view.  
  
 The Orchestration Debugger provides the following functionality:  
  
- Displays a rendered view of the orchestration in which you can replay each processing step for that particular orchestration.  
  
- Enables you to set breakpoints before any orchestration shape and continue execution.  
  
- Enables you to look at specific variables and message data.  
  
- Automatically enables all of the tracking options for a particular orchestration instance when that instance opens in the Orchestration Debugger.  
  
- It gives you the ability to continue, resume in debug, and terminate the particular orchestration instance.  
  
  > [!NOTE]
  >  When you undeploy an assembly, the database maintains the tracking options and breakpoint information for the undeployed assembly. If you subsequently deploy the same assembly, the options and breakpoint information for that assembly are restored.  
  
  The two modes for using the Orchestration Debugger are:  
  
- [Reporting Mode in Orchestration Debugger](../core/reporting-mode-in-orchestration-debugger.md)  
  
- [Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md)  
  
  The capabilities differ depending on the state of the service. You can perform interactive debugging by invoking any service instance currently in the In Breakpoint state, from any view. For information about debugging an orchestration, see [How to Invoke the Orchestration Debugger and the Message Flow Views](../core/how-to-invoke-the-orchestration-debugger-and-the-message-flow-views.md).  
  
## In This Section  
  
-   [Orchestration Debugger User Interface](../core/orchestration-debugger-user-interface.md)  
  
-   [Considerations when Using Orchestration Debugger](../core/considerations-when-using-orchestration-debugger.md)  
  
-   [Working with the Orchestration Debugger View](../core/working-with-the-orchestration-debugger-view.md)