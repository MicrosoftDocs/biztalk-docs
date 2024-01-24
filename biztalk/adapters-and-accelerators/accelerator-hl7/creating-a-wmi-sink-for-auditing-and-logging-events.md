---
description: "Learn more about: Creating a WMI Sink for Auditing and Logging Events"
title: "Creating a WMI Sink for Auditing and Logging Events"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Creating a WMI Sink for Auditing and Logging Events
You can use the following sample code to create a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) sink to monitor auditing and logging events:  
  
 `//Create the WMI query and Event watcher and subscribe to events`  
  
 `ManagementEventWatcher watcher = new ManagementEventWatcher ("root/Default", "select * from  PackageEvent");`  
  
 `ManagementBaseObject evtObj = watcher.WaitForNextEvent();`  
  
 `//Do what you want with the event`  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)
