---
description: "Learn more about: Access Control and Data Security"
title: "Access Control and Data Security"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Access Control and Data Security
BizTalk Server limits access to its processes and databases by using minimum user rights; you can help secure important data in the system by using features from Microsoft Windows Server. For security reasons, BizTalk Server Administrators and BizTalk Hosts should not have more user rights than necessary to perform their jobs.  
  
 BizTalk controls Administrative access to data using SQL roles, thereby controlling access to data both via tools and directly via the database. BizTalk Host access to data is controlled using Host User groups and accounts.  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there are two Administrative Roles: the BizTalk Server Administrator, and the BizTalk Server Operator. Anytime you create a BizTalk Server database through installation or the BizTalk Server Administration Console, BizTalk Server automatically creates SQL roles for both these administrative roles in that database. BizTalk Server grants each role, and any SQL Server login assigned to the role, the minimum user rights needed by administrators on the SQL Server objects (tables, views, stored procedures, etc) to perform administrative tasks on that database.  
  
 The BizTalk Server Administrator is a high privilege role with access to configuration and tracking data. The BizTalk Server Operator is a low privilege role with access only to monitoring and troubleshooting actions. This latter role can view service state and message flow and can start or stop applications and terminate and resume service instances, but cannot change configuration or view message properties and content.  
  
 Similarly, BizTalk Server creates in each database a SQL role for the user group for each host, and grants this role the minimum user rights it needs for the user group to perform tasks for that host.  
  
## In This Section  
  
-   [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)  
  
-   [Access Control for Groups and Service Accounts](../core/access-control-for-groups-and-service-accounts.md)  
  
-   [Access Control for Administrative Roles](../core/access-control-for-administrative-roles.md)  
  
-   [Access Control to Business Information](../core/access-control-to-business-information.md)  
  
-   [Minimum Security User Rights](../core/minimum-security-user-rights.md)
