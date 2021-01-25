---
description: "Learn more about: Orchestration Failures"
title: "Orchestration Failures | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Catch Exception block [Orchestration Designer], suspended orchestrations"
  - "HAT, Catch Exception block [Orchestration Designer]"
  - "Catch Exception block [Orchestration Designer], HAT"
  - "orchestrations, troubleshooting [HAT]"
  - "orchestrations, errors"
  - "HAT, Orchestration Debugger"
  - "Orchestration Debugger"
  - "errors, orchestrations"
  - "HAT, troubleshooting orchestrations"
  - "orchestrations, HAT"
  - "HAT, orchestrations"
ms.assetid: d0a799fb-7859-4774-b444-979f22f04215
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Failures
Orchestrations vary in complexity; for example, an orchestration may call a .NET object or construct messages via transform and assignment shape. As a result, it is impossible to list out every possible failure, due to the variety of its content as well as level of customization. However, all failures encountered in orchestrations appear as exceptions.  
  
 If an orchestration does not include any **CatchException** shape for an exception, the exception causes the orchestration to be Suspended, but not resumable. This means that message and service instance tracking, or a WMI script, cannot recover the instance. However, you can save all messages associated with the Suspended (not Resumable) instance using tracking (or WMI script) for diagnostic and manual retry.  
  
 To diagnose the problem, use the Orchestration Debugger to see the last shape executed before the instance is suspended. You can also view exception details using the Orchestration Debugger.  
  
## See Also  
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)   
 [Debugging an Orchestration](../core/debugging-an-orchestration.md)
