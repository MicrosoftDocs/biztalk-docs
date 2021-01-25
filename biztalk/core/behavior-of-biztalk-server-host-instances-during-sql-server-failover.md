---
description: "Learn more about: Behavior of BizTalk Server Host Instances during SQL Server Failover"
title: "Behavior of BizTalk Server Host Instances during SQL Server Failover | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5642417-d27f-4539-a369-5fa11bec4a4f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Behavior of BizTalk Server Host Instances during SQL Server Failover
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases housed on a clustered instance of Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are temporarily unavailable if the clustered instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] experiences a failover. This section documents the behavior of the host instances associated with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable.  
  
## Behavior of In-Process Host Instances during SQL Server Failover  
 If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable, then an in-process instance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host will be recycled until the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is restored. Once the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases is restored, document processing resumes normally.  
  
## Behavior of Isolated Host Instances During SQL Server Failover  
 If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are unavailable, then an isolated instance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host will pause and an error similar to the following will be generated in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application log:  
  
```  
All receive locations are being temporarily disabled because either   
the MessageBox or Configuration database is not available.   
When these databases become available, the receive locations will be automatically enabled.  
```  
  
 Once the connection to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases is restored an informational message similar to the following is written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application log and document processing resumes normally:  
  
```  
All receive locations are being enabled because both the MessageBox and Configuration databases are back online.  
```  
  
## See Also  
 [Hosts](../core/hosts.md)
