---
description: "Learn more about: Password Synchronization"
title: "Password Synchronization2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, passwords"
  - "passwords, synchronizing [SSO]"
  - "managing [SSO], synchronizing passwords"
  - "Password Synchronization [SSO]"
  - "Password Synchronization [SSO], about Password Synchronization"
  - "SSO database, passwords"
ms.assetid: 6d4970e0-ac73-4fca-ab8f-6c8a6f3a6ec0
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Password Synchronization
The purpose of Password Synchronization is to simplify administration of the SSO database, and to keep passwords in sync across user directories.  
  
 These two tasks are accomplished through the use of password synchronization adapters, and the topics in this section describe the command line utility for creating and managing those adapters.  
  
 There are three types of password synchronization sub-features.  
  
 The first type is **Windows to External** (for example, Active Directory to RACF). In this scenario, a Windows user's password change is captured and sent to the Enterprise SSO Server assigned to receive password changes from domain controllers. This then forwards the password change to an external system and the mapping in the SSO database is kept in sync with the change made on the external system.  
  
 The second type is **External to Windows - Full synchronization**. In this scenario, a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database, and also updates the Windows user's password in Active Directory.  
  
 The third type is **External to Windows - Partial synchronization**. In this scenario a password is captured on the External system and sent to the Enterprise Single Sign-On server assigned for Password Synchronization which then updates the password in the SSO database.  
  
## In This Section  
  
-   [How to Install Password Synchronization](../core/how-to-install-password-synchronization.md)  
  
-   [How to Administer Password Synchronization](../core/how-to-administer-password-synchronization.md)  
  
-   [How to Configure Password Synchronization](../core/how-to-configure-password-synchronization.md)  
  
-   [How to Manage Password Synchronization](../core/how-to-manage-password-synchronization.md)
