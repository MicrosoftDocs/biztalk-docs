---
title: "WCF Adapters Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance, WCF adapters"
  - "performance, performance counters"
  - "WCF adapters, performance"
ms.assetid: 9feb052f-5674-419f-84ab-9b5d312a04a5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters Performance Counters
Performance counters enable you to monitor specific aspects of work performed on the site or system by a service. Performance counters can help you identify and troubleshoot server performance issues. The WCF adapters do not provide their own performance counters. However, you can monitor the performance counters of Windows Communication Foundation (WCF) to gauge the performance of the WCF receive locations. To use the WCF performance counters for the WCF receive locations, you have to enable the performance counters for the host instances running the receive locations.  
  
> [!NOTE]
>  The WCF performance counters are not available for WCF send ports.  
  
 For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file. For the isolated WCF adapters, you can modify the Web.config file to enable the performance counters. For more information about the WCF performance counters, see "WCF Performance Counters" at [http://go.microsoft.com/fwlink/?LinkID=87245](http://go.microsoft.com/fwlink/?LinkID=87245).  
  
## Enabling the WCF Performance Counters for the WCF Receive Locations  
 For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.  
  
 For the isolated WCF adapters, you can enable WCF tracing by modifying the Web.config file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder  
  
 To modify BTSNtSvc.exe.config or Web.config, open the configuration file, and then configure WCF tracing, as indicated in the following configuration example:  
  
> [!NOTE]
>  The BTSNTSvc.exe.config file is always located in the same directory as the BTSNTSvc.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
```  
<configuration>  
 <system.serviceModel>  
 <diagnostics performanceCounters="All" />  
 </system.serviceModel>  
 </configuration>  
```  
  
 The **performanceCounters** attribute can be set to enable a specific type of performance counters. Valid values are  
  
- **All**: All category counters (**ServiceModelService**, **ServiceModelEndpoint**, and **ServiceModelOperation**) are enabled.  
  
- **ServiceOnly**: Only **ServiceModelService** category counters are enabled.  
  
- **Off**: ServiceModel* performance counters are disabled. This is the default value.  
  
  After modifying the BTSNTSvc.exe.config file, you must restart the host instances running the in-process WCF receive locations.  
  
## Types of Performance Counters  
 WCF performance counters are scoped to three different levels: service, endpoint, and operation.  
  
 **Service performance counters**  
  
 Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service. They are found under the **ServiceModelService 3.0.0.0** performance object when viewing with Performance Monitor. The instances are named using the following pattern:  
  
```  
biztalkserviceinstance@<URI of a receive location>  
```  
  
 Because the WCF adapters create a separate service host for each receive location, a performance counter instance is created for each receive location. For more information about the service class implementing the WCF service contracts, see the **BizTalkServiceInstance Class** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
 **Endpoint performance counters**  
  
 Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages. They are found under the **ServiceModelEndpoint 3.0.0.0** performance object when viewing with Performance Monitor. The instances are named using the following pattern:  
  
```  
biztalkserviceinstance.<WCF service contract>@<URI of a receive location>  
```  
  
 A performance counter instance is created for each receive location. In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location. For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 **Operation performance counters**  
  
 Operation performance counters are found under the **ServiceModelOperation 3.0.0.0** performance object when viewing with Performance Monitor. Two performance counter instances are created for each receive location. One of the object instances is named using the following pattern:  
  
```  
biztalkserviceinstance.<WCF service contract>biztalksubmit@<URI of a receive location>  
```  
  
 In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location. **biztalksubmit** is an operation name declared in the service contract, and causes the runtime to create WSDL operations in the metadata.  
  
> [!NOTE]
>  For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 The other object instance is named using the following pattern:  
  
```  
biztalkserviceinstance.<WCF service contract><twowaymethod|onewaymethod>@<URI of a receive location>  
```  
  
 This performance counter instance represents the operation that asynchronously processes messages incoming through the receive location. The operation name part of this instance can be **twowaymethod** or **onewaymethod** depending on the type of WCF adapter used in the receive location. If you use the WCF-NetMsmq adapter, an instance having the **onewaymethod** operation name is created. For the other adapters, **twowaymethod** is used for the operation name part.