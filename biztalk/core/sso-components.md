---
description: "Learn more about: SSO Components"
title: "SSO Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SSO Components
The sub services of the Enterprise Single Sign-On (SSO) service are as follows:  
  
-   **Mapping.** This component maps the user account in the Windows system to the user accounts in the back-end systems.  
  
-   **Lookup.** This component looks up the user credentials in the SSO database in the back-end system. This is the SSO runtime component.  
  
-   **Administration.** This component manages the affiliate applications and the mappings for each affiliate application.  
  
-   **Secret.** This component generates the master secret and distributes it to the other SSO servers in the system. It is only active on the Single Sign-On server that is acting as the master secret server.  
  
-   **Password Synchronization.** This component simplifies administration of the SSO database, and keeps passwords in sync across user directories.  
  
## See Also  
 [SSO Server](../core/sso-server.md)   
 [Installing SSO](../core/installing-sso.md)
