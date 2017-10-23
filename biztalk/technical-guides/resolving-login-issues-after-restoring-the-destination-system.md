---
title: "Resolving Login Issues After Restoring the Destination System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9232ca3-dadb-4b3c-8ec4-4e307c32d2e5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Resolving Login Issues After Restoring the Destination System
Depending on how the source system was configured during deployment, "orphaned" users may need to be resolved. An orphaned database user is a user who does not have a corresponding security login in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Create corresponding logins for these users before bringing the system online using the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] SQL Management Studio (in **Security**, **Logins**). You can create these logins at any point, but we recommend that you create them when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping is configured.  
  
 The logins that are created should correspond to the Windows accounts and groups that were used when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] was configured on the source system and to any logins that were manually created and used in any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-created role. If these logins correspond to local Windows accounts or groups, the accounts and groups must first be created before the login can be added. If the computer name for the BizTalk server is not changed, then resolve the users associated with the logins for the local accounts and groups.  
  
 When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, follow the steps in Microsoft Knowledge Base Article 918992 [How to transfer the logins and the passwords between instances of SQL Server 2005 and SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=157143) to create a script that will add the necessary logins to the destination server.  
  
## See Also  
 [Troubleshooting Log Shipping](../technical-guides/troubleshooting-log-shipping.md)
