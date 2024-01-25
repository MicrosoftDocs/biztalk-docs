---
description: "Learn more about: Domain Groups in BizTalk"
title: "Domain Groups"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Domain Groups in BizTalk
BizTalk Server supports domain group and user accounts in both single and multiple computer configurations. For multiple computer configurations, you must observe the requirements provided in this section and in the Considerations for Multiserver Environments in the Installation Guide. For more information, see the [installation overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).  
  
## Before you begin
-   If you use domain groups for your BizTalk Server configuration, you must manually create the groups before you configure BizTalk Server. The Configuration Manager cannot create domain groups.  
  
-   After creating domain groups and/or user accounts, add user accounts to the proper groups according to the group affiliations in [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Use **\<DomainName\>\\<UserName\>** when specifying domain account information in the Configuration Manager.  
  
-   BizTalk Server requires domain accounts for all clustering scenarios. You cannot use local accounts with clustered SQL Server or clustered SSO Server (master secret server).  
  
-   The administrator installing and configuring BizTalk Server must be a member of the following groups: SSO Administrators (only when configuring the master secret server); local Administrators; sysadmin SQL Server role; OLAP Administrators.  
  
> [!NOTE]
>  You can create the domain group automatically if you specify a domain group during configuration for the SSO Administrators and SSO Affiliate Administrators, and you have sufficient privileges. If you do not have sufficient privileges, ensure that these groups already exist.  
  
## See Also  
 [Local Groups](../core/local-groups.md)   
 [Installation Overview](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)
