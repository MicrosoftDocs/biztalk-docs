---
title: "Access Control for Groups and Service Accounts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "access control, service accounts"
  - "user accounts, default accounts"
  - "service accounts, security"
  - "user accounts, unsupported"
  - "access control, groups"
  - "service accounts, access control"
  - "groups, access control"
  - "groups, security"
ms.assetid: 411a7bfa-6675-4d09-9e37-83e2941df3c6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Access Control for Groups and Service Accounts
Each BizTalk Host instance runs under a user-created service account. You must provide the service accounts and their passwords at the time you create the host instance on a computer. BizTalk Server then ensures that the accounts have the minimum user rights needed to do their jobs by adding each of these service accounts to a local or domain Windows group that, in turn, it adds to the SQL Server Database role specific to that host.  
  
 This approach offers the following benefits:  
  
- You can give each host instance a distinct service account, making it possible to change the passwords for each host instance without having to take servers offline. You can perform rolling password updates without interrupting service.  
  
  > [!NOTE]
  >  You cannot use the same service account for hosts that are authentication trusted and hosts that are not authentication trusted.  
  
- If you grant resource user rights to the local or domain group at the Microsoft SQL Server™ level, you can add and subtract service accounts without having to change the user rights granted in SQL Server, thus reducing your management burden and total cost of ownership.  
  
  To ensure that the service accounts have the minimum user rights they need to do their jobs, the SQL Server Database roles that BizTalk Server creates for the service accounts are not identical on all the BizTalk Server databases. For the Management and Tracking databases, all of the host instance service accounts need access to the same SQL Server objects, so BizTalk Server created a single SQL Server Database role named BTS_Host_User. BizTalk adds all the Windows groups created for BizTalk hosts to this SQL Server Database role.  
  
  For the MessageBox database, each host has some resources dedicated to that host. BizTalk Server creates a SQL Server Database role per host, named BTS_\<*hostname*\>_User, and adds the Windows group for each host to its respective SQL Server Database role in order to block access of one host resources by another host.  
  
## Accounts not supported by BizTalk Server  
 BizTalk Server does not support using any of the following built-in Windows accounts:  
  
-   NT_AUTHORITY\NetworkService  
  
-   LocalSystem  
  
-   NT_AUTHORITY\LocalService  
  
## See Also  
 [Access Control for Administrative Roles](../core/access-control-for-administrative-roles.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Access Control and Data Security](../core/access-control-and-data-security.md)