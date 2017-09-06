---
title: "Best Practices for Managing Windows Groups and User Accounts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, Windows groups"
  - "authenticating, best practices"
  - "Windows groups, security"
  - "best practices, user accounts"
  - "best practices, security"
  - "security, best practices"
  - "user accounts, security"
  - "authenticating, security"
  - "Windows groups, best practices"
  - "best practices, authenticating"
  - "user accounts, best practices"
  - "hosts, security"
  - "hosts, best practices"
  - "best practices, hosts"
ms.assetid: 0c4a141e-97ce-434a-8e45-a56c634bbd6c
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Managing Windows Groups and User Accounts
This section contains best practices and tips for managing security for Windows groups and user accounts.  
  
-   **Use service accounts with minimum privileges necessary for host instances**  
  
     To help ensure the security of your BizTalk Server environment, we recommend that you use service accounts with the minimum privileges necessary to run host instances. For more information about the minimum privileges that service accounts require, see [Access Control and Data Security](../core/access-control-and-data-security.md).  
  
-   **Use different user groups for authentication trusted and non-trusted hosts**  
  
     To ensure that non-authentication trusted hosts have fewer privileges than authentication trusted hosts, you must use different service accounts for each host.  
  
-   **Use a different user group for each BizTalk Host**  
  
     To maximize the security boundary between hosts, we recommend that you use a different Windows user group for each BizTalk Host in your BizTalk group.  
  
-   **Remove the installation user from the BizTalk Server Administrators group**  
  
     When you install BizTalk Server on a single computer with local groups, the user performing an interactive installation of BizTalk Server is automatically added to the BizTalk Server Administrators group. This allows that user to configure BizTalk Server with the Configuration Manager.  
  
     If the user who installs BizTalk Server will not be administering BizTalk Server, we recommend that you remove this user from the BizTalk Server Administrators group after BizTalk Server is configured.  
  
## See Also  
 [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md)