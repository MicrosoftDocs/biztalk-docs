---
title: "Administrative Tasks (WMI)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f31cd7af-e8df-408c-ae3b-64b79d310109
caps.latest.revision: 3
---
# Administrative Tasks (WMI)
Using the Windows Management Instrumentation (WMI) providers for Host Integration Server, you can administer a variety of components on Host Integration Server. However, any administration you perform on Host Integration Server through WMI is performed through the following tasks:  
  
-   Logging on to WMI  
  
     Like most providers, you must first log on to the WMI provider to use it. Therefore, the WMI providers expose the logon and security interfaces. For more information, see [Logging on to Host Integration Server Through a WMI Provider](../HIS2010/logging-on-to-host-integration-server-through-a-wmi-provider1.md).  
  
-   Getting and setting information  
  
     Most of the tasks you will do through WMI will be checking information about different Host Integration Server services. You can also set information. For more information, see [Accessing a Host Integration Server Property through WMI](../HIS2010/accessing-a-host-integration-server-property-through-wmi1.md).  
  
-   Calling methods  
  
     The methods exposed on the WMI providers for Host Integration Server are designed mainly to administer various Host Integration Server services. You can administer these services by calling the relevant **Start**, **Stop**, **Pause**, or **Cancel** method through the relevant provider. For more information, see [Calling a Host Integration Server Method through WMI](../HIS2010/calling-a-host-integration-server-method-through-wmi2.md).