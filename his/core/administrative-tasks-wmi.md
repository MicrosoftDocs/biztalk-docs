---
title: "Administrative Tasks (WMI)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80250217-51fe-46ba-9069-c249e98a1338
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Administrative Tasks (WMI)
Using the Windows Management Instrumentation (WMI) providers for Host Integration Server, you can administer a variety of components on Host Integration Server. However, any administration you perform on Host Integration Server through WMI is performed through the following tasks:  
  
-   Logging on to WMI  
  
     Like most providers, you must first log on to the WMI provider to use it. Therefore, the WMI providers expose the logon and security interfaces. For more information, see [Logging on to Host Integration Server Through a WMI Provider](../core/logging-on-to-host-integration-server-through-a-wmi-provider.md).  
  
-   Getting and setting information  
  
     Most of the tasks you will do through WMI will be checking information about different Host Integration Server services. You can also set information. For more information, see [Accessing a Host Integration Server Property through WMI](../core/accessing-a-host-integration-server-property-through-wmi.md).  
  
-   Calling methods  
  
     The methods exposed on the WMI providers for Host Integration Server are designed mainly to administer various Host Integration Server services. You can administer these services by calling the relevant **Start**, **Stop**, **Pause**, or **Cancel** method through the relevant provider. For more information, see [Calling a Host Integration Server Method through WMI](../core/calling-a-host-integration-server-method-through-wmi.md).