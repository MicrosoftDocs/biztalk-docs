---
title: "Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8822c1e4-d146-4361-b25a-7b81cd5cdd3b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking
> [!NOTE]  
>  This topic is applicable only for Windows Server 2003.  
  
 You should disable the Windows Server 2003 Service Pack 1 and Service Pack 2 denial of service checking. This is because under certain high-load scenarios, Windows Server 2003 SP1 and SP2 denial of service checking may incorrectly identify valid TCP/IP connections as a denial of service attack.  
  
> [!IMPORTANT]  
>  You should disable this feature only in an intranet scenario when you are sure you will not suffer from actual denial of service attacks.  
  
## How Denial of Service Can Affect TCP/IP Connections  
 Windows Server 2003 SP1 and SP2 implement a security feature that reduces the size of the queue for concurrent TCP/IP connections to the server. This feature helps prevent denial of service attacks. Under heavy load conditions, the TCP/IP protocol in Windows Server 2003 SP1 or later may incorrectly identify valid TCP/IP connections as a denial of service attack. This may occur when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is under heavy load.  
  
## Modifying the Registry Entry  
 For more information, see Microsoft Knowledge Base article 899599, ["A BizTalk Server Host instance fails, and a 'General Network' error is written to the Application log when the BizTalk Server-based server processes a high volume of documents"](http://go.microsoft.com/fwlink/?LinkId=158860) (<http://go.microsoft.com/fwlink/?LinkId=158860>). Follow the instructions in this article to create the **SynAttackProtect** registry entry on computers running SQL Server that host [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and on any computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that are running Windows Server 2003 SP1 or later.  
  
## Tuning Registry Settings that Govern the Level of Denial of Service Attack Protection  
 In certain scenarios you may want to maintain denial of service protection but reduce how aggressively the denial of service functionality is applied. It is possible to tune the default behavior of the denial of service protection feature by following these steps:  
  
1.  Ensure that the **SynAttackProtect** registry entry is set to a REG_DWORD value of **1** as described at [http://go.microsoft.com/fwlink/?LinkId=111477](http://go.microsoft.com/fwlink/?LinkId=111477).  
  
2.  Configure the **TcpMaxHalfOpen** registry entry as described at [http://go.microsoft.com/fwlink/?LinkId=111478](http://go.microsoft.com/fwlink/?LinkId=111478).  
  
3.  Configure the **TcpMaxHalfOpenRetried** registry entry as described at [http://go.microsoft.com/fwlink/?LinkId=111479](http://go.microsoft.com/fwlink/?LinkId=111479).  
  
## See Also  
 [Operational Readiness Checklists](../technical-guides/operational-readiness-checklists.md)