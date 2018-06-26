---
title: "Considerations when Using Orchestration Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Orchestration Debugger, modified orchestrations"
  - "Orchestration Debugger, planning"
  - "atomic scopes"
  - "planning, Orchestration Debugger"
  - "Orchestration Debugger, atomic scopes"
  - "Orchestration Debugger, simple types"
  - "orchestrations, modifying"
ms.assetid: 55bfef48-08bd-48bb-abd5-7264e683da46
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations when Using Orchestration Debugger
Following are some things to consider when you work with the Orchestration Debugger.  
  
## Tracking atomic scopes  
 An orchestration can contain atomic scopes to include calls to the Rule Engine. When you attach to an instance in the orchestration debugger, any atomic scopes in the orchestration instance will cause gaps to appear in the tracked events list. This happens for two reasons:  
  
- Because events for the shapes inside atomic transactions do not get persisted until the scope commits  
  
- The debugger reloads events onto the end of the list, so any gaps remain unfilled during the live session.  
  
  You can eliminate the gaps if you refresh the view.  
  
> [!NOTE]
>  You cannot set a breakpoint on shapes inside an atomic scope.  
  
## Setting breakpoints in the exception handler scope  
 If the breakpoint is set at the exception catch handler, the exception types must be marked as serializable, or the orchestration debugger will not stop at the breakpoints you set. This is because of that the orchestration debugger does persistence at the breakpoint, therefore, when there is a non-serializable object in the orchestration instance state, a persistence exception will be thrown, and in this case, you will also receive a DebugBreakPointFailedException exception.  
  
## Tracking a modified orchestration  
 If you track an orchestration modified without changing the version number, you must restart all the host instances to which the orchestration is enlisted. This insures that any shape change in the newly deployed version displays correctly, as you step through the Orchestration Debugger.  
  
## Tracking simple types  
 The Orchestration Debugger only supports simple types. For example, if you track a multipart message that contains a .NET object you can view the properties of all message parts, with the exception of the .NET object properties.  
  
 When an orchestration appears in the In Breakpoint state and the Orchestration Debugger starts, you can perform the following actions:  
  
-   Use the **Attach** service option.  
  
-   Review the steps that have already completed.  
  
-   View the state of variables and messages.  
  
-   Set additional breakpoints.  
  
-   Select the **Continue Service** option.  
  
-   Repeat any steps as required.  
  
## See Also  
 [Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md)   
 [Debugging an Orchestration](../core/debugging-an-orchestration.md)