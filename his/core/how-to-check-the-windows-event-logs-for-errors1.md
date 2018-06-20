---
title: "How to Check the Windows Event Logs for Errors1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f68fae1d-f19a-46b7-8ab3-6922e1043f7a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Check the Windows Event Logs for Errors
The Windows Event Log keeps a record of the system's behavior. It contains:  
  
- Informational events that signal normal system function. For instance, certain services log an event whenever they start or shut down.  
  
- Warning events that signal issues that can be problematic but are not actual errors.  
  
- Errors. If you find any error events in your logs, this indicates a problem.  
  
  .NET sometimes logs error events when a problem is detected in an application. This is the main way of signaling a problem or giving diagnostic information. Therefore, understanding a .NET problem begins with searching the event log for errors.  
  
### To search for errors in the event logs  
  
1.  Search for a red circle that contains an x. Errors generally indicate a serious problem, so you should troubleshoot them before moving on to the specific problem.  
  
     Search the event logs for .NET errors. .NET generally logs its events in the Application and System logs. You can determine which errors are from .NET by looking at the Source column. Errors with a source heading of .NET or MSDTC are .NET errors. Explore the .NET errors by double-clicking the error to bring up an error dialog box that contains all the error information: Source, Machine, Date, Time, and Event ID. At the bottom of the error dialog box is an error description. Read this carefully as it will explain the error and even recommend a remedy. Also, check the Data area on the error dialog box; it may contain additional useful binary information.  
  
2.  Determine whether the error contains a call stack. A call stack is a piece of text describing what the application was doing when the error occurred. It begins with a Call stack line. If there is a call stack, determine which .dll file caused the error. Each line in the call stack begins with the name of a .dll file and ends with an exclamation mark or a plus sign.  
  
     The call stack shows a cause and effect chain. The .dll file listed in the top line in the call stack is the direct cause of the error, and .dll files listed on lines below it are indirect causes of the error.  
  
## See Also  
 [Windows Event Viewer](../core/windows-event-viewer1.md)