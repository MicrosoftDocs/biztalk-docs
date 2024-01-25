---
description: "Learn more about: Enterprise Single Sign-On (SSO)"
title: "Enterprise Single Sign-On (SSO)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Enterprise Single Sign-On (SSO)
Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local and network boundaries, including domain boundaries. SSO stores the credentials in the SSO database. Because SSO provides a generic single sign-on solution, middleware applications and custom adapters can leverage SSO to securely store and transmit user credentials across the environment. End users do not have to remember different credentials for different applications.  
  
 The Single Sign-On system consists of an SSO database, a master secret server, and one or more Single Sign-On servers.  
  
 The SSO system contains *affiliate applications* that an administrator defines. An *affiliate application* is a logical entity that represents a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using Enterprise Single Sign-On. Each affiliate application has multiple user mappings; for example, it has the mappings between the credentials for a user in Active Directory and their corresponding RACF credentials.  
  
 The SSO database is the SQL Server database that stores the information about the affiliate applications, as well as all of the encrypted user credentials to all the affiliate applications.  
  
 The *master secret server* is the Enterprise Single Sign-On server that stores the master secret. All other Single Sign-On servers in the system get the master secret from the master secret server.  
  
 The SSO system also contains one or more SSO Servers. These servers do the mapping between the Microsoft Windows and back-end credentials, and look up the credentials in the SSO database. Administrators use them to maintain the SSO system.  
  
 For more a complete look at Enterprise Single Sign-On, see [Understanding SSO](../core/understanding-sso.md).  
  
## See Also  
 [Runtime Architecture](../core/runtime-architecture.md)
