---
title: "Creating a WMI Sink for Auditing and Logging Events | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WMI sink"
  - "auditing, WMI sink"
  - "WMI sink, auditing"
  - "logging, WMI sink"
  - "WMI sink, logging"
ms.assetid: 5feb1e98-32ed-4505-878e-274028d50c3c
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a WMI Sink for Auditing and Logging Events
You can use the following sample code to create a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) sink to monitor auditing and logging events:  
  
 `//Create the WMI query and Event watcher and subscribe to events`  
  
 `ManagementEventWatcher watcher = new ManagementEventWatcher ("root/Default", "select * from  PackageEvent");`  
  
 `ManagementBaseObject evtObj = watcher.WaitForNextEvent();`  
  
 `//Do what you want with the event`  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)