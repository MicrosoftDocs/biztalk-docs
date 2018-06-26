---
title: "Planning for Database Testing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4cf5e1f-a960-4702-a050-a2cdacddcbca
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Database Testing
Thorough stress/load testing of a BizTalk solution figures prominently in the ultimate success or failure of the solution. Since [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance is so dependent on the performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, testing and optimization of a BizTalk solution frequently focuses on testing and optimization of the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
## Considerations When Planning for Database Testing  
 Consider the following when planning for database testing:  
  
1. **Ensure that the test environment matches the production environment as closely as possible.** Using a virtual environment such as Microsoft Hyper-V Server 2008 for unit testing is perfectly acceptable; however, all load/stress testing should be performed against hardware that matches the final production environment as closely as possible.  
  
2. **Plan to measure maximum sustainable throughput and maximum sustainable tracking throughput of the BizTalk Server system**. Maximum sustainable throughput is measured as the highest load of message traffic that the BizTalk Server system can handle indefinitely in production. Follow the steps in the following topics in BizTalk Server Help:  
  
   - [Measuring Maximum Sustainable Engine Throughput](http://go.microsoft.com/fwlink/?LinkID=154388) (http://go.microsoft.com/fwlink/?LinkID=154388).  
  
   - [Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815).  
  
     These topics describe the methodology for generating load against the system, the parameters that should be measured, and general recommendations to follow when testing MST.  
  
3. **Understand the implications of how BizTalk Server**  
    **implements host throttling.** The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host throttling algorithm attempts to moderate the workload of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instances to ensure that the workload does not exceed the capacity of the host instance or any downstream host instances. The throttling mechanism is self tuning and the default configuration options are suitable for the majority of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processing scenarios. You should, however, have a good understanding of the throttling mechanism before implementing load/stress testing. For more information, see [Optimizing Resource Usage Through Host Throttling](http://go.microsoft.com/fwlink/?LinkId=155770) (<http://go.microsoft.com/fwlink/?LinkId=155770>) in BizTalk Server Help.