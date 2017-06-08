---
title: "Domain Groups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "domain groups"
ms.assetid: 9adc090e-e18c-46b6-b985-49b200d42966
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Domain Groups
BizTalk Server supports domain group and user accounts in both single and multiple computer configurations. For multiple computer configurations, you must observe the requirements provided in this section and in the Considerations for Multiserver Environments in the Installation Guide. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](../Topic/Installation%20Overview%20for%20BizTalk%20Server%202013%20and%202013%20R2.md).  
  
-   If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server. The Configuration Manager cannot create domain groups.  
  
-   After creating domain groups and/or user accounts, add user accounts to the proper groups according to the group affiliations in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Use **\<DomainName>\\<UserName\>** when specifying domain account information in the Configuration Manager.  
  
-   BizTalk Server requires domain accounts for all clustering scenarios. You cannot use local accounts with clustered SQL Server or clustered SSO Server (master secret server).  
  
-   The administrator installing and configuring BizTalk Server must be a member of the following groups: SSO Administrators (only when configuring the master secret server); local Administrators; sysadmin SQL Server role; OLAP Administrators.  
  
> [!NOTE]
>  You can create the domain group automatically if you specify a domain group during configuration for the SSO Administrators and SSO Affiliate Administrators, and you have sufficient privileges. If you do not have sufficient privileges, ensure that these groups already exist.  
  
## See Also  
 [Local Groups](../core/local-groups.md)   
 [Installation Overview for BizTalk Server 2013 and 2013 R2](../Topic/Installation%20Overview%20for%20BizTalk%20Server%202013%20and%202013%20R2.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)