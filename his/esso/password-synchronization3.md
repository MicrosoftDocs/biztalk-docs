---
description: "Learn about Password Synchronization, that is used to simplify the administration of the Single Sign-On (SSO) credential database."
title: "Password Synchronization3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bfb82d0-77d2-4e53-bd47-e8734e682041
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Password Synchronization

The purpose of Password Synchronization is to simplify administration of the Single Sign-On (SSO) credential database, and to keep passwords in sync across user directories. You can accomplish these two tasks by using password synchronization adapters. The topics in this section describe the command-line utility for creating and managing those adapters.  
  
 There are three types of password synchronization sub-features.  
  
 The first type is **Windows to External** (for example, Active Directory to RACF). In this scenario, a Windows user's password change is captured and sent to the Enterprise SSO server that is assigned to receive password changes from domain controllers. This server then forwards the password change to an external system, and the mapping in the SSO credential database is kept in sync with the change made on the external system.  
  
 The second type is **External to Windows - Full synchronization**. In this scenario, a password is captured on the External system and sent to the Enterprise Single Sign-On server that is assigned for Password Synchronization. It then updates the password in the SSO credential database, and also updates the Windows user's password in Active Directory.  
  
 The third type is **External to Windows - Partial synchronization**. In this scenario, a password is captured on the External system and sent to the Enterprise Single Sign-On server that is assigned for Password Synchronization. It then updates the password in the SSO credential database.  
  
## In This Section  
  
- [Installing Password Synchronization](../esso/installing-password-synchronization.md)  
  
- [Administering Password Synchronization](../esso/administering-password-synchronization.md)  
  
- [Configuring Password Synchronization](../esso/configuring-password-synchronization.md)  
  
- [Managing Password Synchronization](../esso/managing-password-synchronization.md)
