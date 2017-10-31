---
title: "SSO Components | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0a13b5b-6c73-4b0d-b05e-fc9a395d6196
caps.latest.revision: 3
---
# SSO Components
The sub services of the Enterprise Single Sign-On (SSO) service are as follows:  
  
-   **Mapping.** Maps the user account in the Windows system to the user accounts in the back-end systems (affiliate applications).  
  
-   **Lookup.** Looks up the user credentials in the Credential database in the back-end system. This is the SSO runtime component.  
  
-   **Administration.** Manages the affiliate applications and the mappings for each affiliate application.  
  
-   **Secret.** Generates the master secret and distributes it to the other SSO servers in the system. It is only active on the Single Sign-On server that is acting as the master secret server.  
  
-   **Password Synchronization.** Simplifies administration of the SSO credential database, and keeps passwords in sync across user directories.  
  
## See Also  
 [Enterprise Single Sign-On Basics](../esso/enterprise-single-sign-on-basics.md)   
 [SSO Server](../esso/sso-server.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)