---
title: "How to Create Service Accounts for New Hosts and Host Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Configuration Manager, service accounts"
  - "Windows groups, service accounts"
  - "Configuration Manager"
  - "service accounts, Windows groups"
  - "hosts, service accounts"
  - "service accounts, hosts"
  - "service accounts, Configuration Manager"
  - "service accounts, creating"
  - "creating, service accounts"
ms.assetid: cef97f4a-8db1-41b6-9614-608c2fbf59a9
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Service Accounts for New Hosts and Host Instances
The Configuration Manager configures the necessary Windows groups and user accounts when you install and configure BizTalk Server on a single computer.  
  
 You must manually create Windows groups and user accounts, and add the user accounts to the Windows groups in a domain environment before running the Configuration Manager. For more information, see [Domain Groups](../core/domain-groups.md).  
  
 You must perform the following procedure before creating a new host or host instance.  
  
## Prerequisites  
 You must be logged on as a member of Administrators or Domain Admins group to perform this procedure.  
  
### To create service accounts for new hosts or host instances  
  
1.  Create a host Windows group for the new host that you will create. For more information about creating a new host, see [How to Create a New Host](../core/how-to-create-a-new-host.md).  
  
2.  Create service accounts for each host instance that will be added to the new host. For more information about creating a new host instance, see [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).  
  
3.  Add the service accounts to the host Windows group as needed. For information about the Windows groups to which you must add the service account, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
4.  Use the Windows group and service account when creating the host and host instances.  
  
    > [!NOTE]
    >  Do not specify \<*computer name*\>\ as the prefix in a single computer setup with local groups.  
  
    > [!NOTE]
    >  If you are using a Domain group, you must specify \<*Domain NetBIOS Name*\>\ as the prefix for the host Windows Group name. For example, CONTOSO\btssvc.  
  
## See Also  
 [Managing Hosts and Service Accounts](../core/managing-hosts-and-service-accounts.md)   
 [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)   
 [How to Manage the BizTalk Server Administrators Group](../core/how-to-manage-the-biztalk-server-administrators-group.md)   
 [Best Practices for Managing Windows Groups and User Accounts](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)