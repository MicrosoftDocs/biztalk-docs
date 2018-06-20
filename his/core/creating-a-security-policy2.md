---
title: "Creating a Security Policy2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a3e6fae-8e09-4467-8607-1aaf929b26f9
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Creating a Security Policy
You can create and manage security policy definitions in the **Security Policies** node in the HIP (host-initiated processing) Console.  
  
 When the HIP Console is first started, the **Security Policies** node is empty. The **Security Policies** node contains definitions for how Windows security credentials are established before the execution of the server object. The source of the security credentials can be the following:  
  
- Based on User IDs and Passwords delivered to HIP by the client application program.  
  
- Based on User IDs and Passwords delivered to HIP by well-defined host protocol standards (SNA attach header: FMH5).  
  
- Default host-based User ID and Password.  
  
- Windows credentials that the HIP application runs under  
  
  When host-based credentials are used, the Windows credentials are obtained by using the Single Sign-On (SSO) feature. This feature translates host-based User ID, Password and SSO Affiliated Application ID to a security identification number (SID) that is representative of the Window credentials. The server object is then executed with the translated security credentials.  
  
  You can create a new security policy by using the **Security Policy Wizard**.  
  
## See Also  
 [Working with Host-Initiated Processing](../core/working-with-host-initiated-processing1.md)