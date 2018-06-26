---
title: "Low-Latency Scenario Optimizations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd2a891a-ee4b-4542-b3ce-434e2a6474be
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Low-Latency Scenario Optimizations
By default, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is optimized for throughput rather than low-latency. The following optimizations were applied to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for the test scenario used for this guide.  
  
> [!NOTE]  
>  These optimizations will improve latency but may do so at some cost to overall throughput.  
  
## Increase the BizTalk Server host internal message queue size  
 Each BizTalk host has its own internal in-memory queue. Increase the size of this queue from the default value of 100 to 1000 to improve performance for a low-latency scenario. For more information about modifying the value of the internal message queue size, see “How to Modify the Default Host Throttling Settings” in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkID=120225](http://go.microsoft.com/fwlink/?LinkID=120225).  
  
## Reduce the MaxReceiveInterval value in the adm_ServiceClass table of the BizTalk Server management database  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses a polling mechanism to receive messages from its host queues in the Messagebox. The **MaxReceiveInterval** value in the adm_ServiceClass table of the BizTalk Management (BizTalkMgmtDb) database is the maximum value in milliseconds that each BizTalk host instance will wait until it polls the MessageBox. The adm_ServiceClass table contains a record for the following service types:  
  
- **XLANG/S** – for BizTalk orchestration host instances  
  
- **Messaging InProcess** – for in-process host instances  
  
- **MSMQT** – for MSMQT adapter host instances  
  
- **Messaging Isolated** – for out of process host instances, used by the HTTP, SOAP, and certain WCF receive adapter handlers  
  
  By default, this value is set to 500 milliseconds, which is optimized for throughput rather than low-latency. In certain scenarios, latency can be improved by reducing this value.  
  
> [!NOTE]
>  Changes to this value impact all instances of the associated service type, therefore, take care to evaluate the impact on all host instances before changing this value.  
> 
> [!NOTE]
>  This value is only used if the Messagebox has no remaining unprocessed messages. If there is a constant backlog of unprocessed messages in the Messagebox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will attempt to process the messages without waiting on the polling delay. After all messages are processed, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will begin polling using the value specified for MaxReceiveInterval.  
> 
> [!NOTE]
>  In a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with a high ratio of host instances to Messagebox database instances, decreasing the value for MaxReceiveInterval may cause excessive CPU utilization on the SQL Server computer that houses the Messagebox database instance. For example, if the MaxReceiveInterval is decreased to a low value (\< 100) in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment with a single Messagebox and > 50 host instances, CPU utilization on the SQL Server may climb above 50%. This phenomenon can occur because the overhead associated with continually polling host queues is significant. If you reduce MaxReceiveInterval to a value less than 100, you should also evaluate the impact that this has on your SQL Server computer’s CPU utilization.