---
title: "Managing Hosts and Service Accounts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, managing"
  - "managing [user accounts]"
  - "service accounts, security"
  - "managing [hosts], security"
  - "security, hosts"
  - "managing [Windows groups]"
  - "hosts, security"
  - "security, service accounts"
  - "Windows groups, managing"
  - "user accounts, managing"
ms.assetid: 25797571-f1f9-42a4-8fff-5b03076bbe36
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing Hosts and Service Accounts
After you configure BizTalk Server, you must manage Windows groups and user accounts. This section provides information about how to manage these accounts for BizTalk Server.  
  
> [!NOTE]
>  For a multiserver installation of BizTalk Server you must use a Domain Global group. For a single server installation of BizTalk Server you can use either a Domain Global group or a local group.  
  
 You must be a Windows administrator to perform the following tasks:  
  
- Create a host Windows group  
  
- Create service accounts for each host instance  
  
- Add the service accounts to the host Windows group  
  
- Modify the Windows group associated with the host  
  
  For a complete list and description of the groups and their affiliated user accounts in the BizTalk Server, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
  For more information the minimum security user rights for administrative tasks, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## In This Section  
  
-   [How to Create Service Accounts for New Hosts and Host Instances](../core/how-to-create-service-accounts-for-new-hosts-and-host-instances.md)  
  
-   [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md)