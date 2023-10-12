---
description: "Learn more about: SSO Server"
title: "SSO Server"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SSO Server
The Enterprise Single Sign-On (SSO) server can perform any of the following tasks:  
  
-   **Functions as the master secret server.** The master secret server holds the master secret, or encryption key, used to encrypt all the credentials in the SSO system. Though the master secret server can act as a server for lookups and administration, it is recommended that you use this server to act only as a master secret server for security reasons. For more information about the functions the master secret server performs, see [Master Secret Server](../esso/master-secret-server.md).  
  
-   **Performs administrative operations.** SSO administrators can use any of the Single Sign-On Servers to perform administrative tasks such as managing affiliate applications, setting user credentials, and managing user mappings.  
  
-   **Performs lookup operations.** The SSO server uses the runtime component to look up the user credentials.  
  
-   **Issues and Redeems Tickets.** The SSO server also issues and redeems SSO tickets, which applications can use to get user credentials.  
  
-   **Password Synchronization.** You can create and manage password synchronization adapters on the SSO Server.  
  
## See Also  
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)   
 [SSO Tickets](../esso/sso-tickets.md)   
 [Master Secret Server](../esso/master-secret-server.md)   
 [Password Synchronization](../esso/password-synchronization3.md)
