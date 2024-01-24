---
description: "Learn more about: SSO Server"
title: "SSO Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SSO Server
The Enterprise Single Sign-On (SSO) server can perform any of the following tasks:  
  
-   **Functions as the master secret server.** The master secret server holds a persisted copy of the master secret, or key, used to encrypt all the credentials in the SSO system. Though the master secret server can act as a server for lookups and administration, it is recommended to use this server to act only as a master secret server for security reasons. For more information about the functions the master secret server performs, see [Master Secret Server](../core/master-secret-server.md).  
  
-   **Performs administrative operations.** SSO administrators can use any of the Single Sign-On Servers to perform administrative tasks such as managing affiliate applications, setting user credentials, and managing user mappings.  
  
-   **Performs lookup operations.** The SSO server uses the runtime component to look up the user credentials.  
  
-   **Issues and Redeems Tickets.** The SSO server also issues and redeems SSO tickets.  
  
-   **Password Synchronization.** You can create and manage password synchronization adapters on the SSO Server.  
  
## See Also  
 [Using SSO](../core/using-sso.md)   
 [Installing SSO](../core/installing-sso.md)
