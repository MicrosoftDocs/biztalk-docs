---
description: "Learn more about: Understanding SSO"
title: "Understanding SSO"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Understanding SSO
To understand Enterprise Single Sign-On, it is useful to look at the three types of Single Sign-On services available today: Windows integrated, extranet, and intranet. These are described below, with Enterprise Single Sign-On falling into the third category.  
  
## Windows Integrated Single Sign-On  
 These services enable you to connect to multiple applications within your network that use a common authentication mechanism. These services request and verify your credentials after you log into the network, and use your credentials to determine the actions that you can perform based on your user rights. For example, if applications integrate using Kerberos, after the system authenticates your user credentials you can access any resource in the network that is integrated with Kerberos.  
  
## Extranet Single Sign-On (Web SSO)  
 These services enable you to access resources over the Internet by using a single set of user credentials. The user provides a set of credentials to log on to different Web sites that belong to different organizations. An example of this type of Single Sign-On is Windows Live ID for consumer based applications. For federated scenarios, Microsoft Active Directory Federation Services enables Web SSO.  
  
## Server-Based Intranet Single Sign-On  
 These services enable you to integrate multiple heterogeneous applications and systems within the enterprise environment. These applications and systems may not use common authentication. Each application has its own user directory store. For example, in an organization, Windows uses Active Directory directory service to authenticate users, and mainframes use IBM's Resource Access Control Facility (RACF) to authenticate the same users. Within the enterprise, middleware applications integrate the front-end and back-end applications. Enterprise Single Sign-On enables users in the enterprise to connect to both the front end and back end while using only one set of credentials. It enables both Windows Initiated Single Sign-On (in which the initial request is made from the Windows domain environment) and Host Initiated Single Sign-On (in which the initial request is made from a non-Windows domain environment) to access a resource in the Windows domain.  
  
 In addition, **Password Synchronization** simplifies administration of the SSO database, and keeps passwords in sync across user directories. This is done through the use of password synchronization adapters, which you can configure and manage using the Password Synchronization tools.  
  
## The Enterprise Single Sign-On System  
 Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local and network boundaries, including domain boundaries. SSO stores the credentials in the SSO database. Because SSO provides a generic single sign-on solution, middleware applications and custom adapters can leverage SSO to securely store and transmit user credentials across the environment. End users do not have to remember different credentials for different applications.  
  
 The Single Sign-On system consists of an SSO database, a master secret server, and one or more Single Sign-On servers.  
  
 The SSO system contains affiliate applications that an administrator defines. An affiliate application is a logical entity that represents a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using Enterprise Single Sign-On. Each affiliate application has multiple user mappings; for example, it has the mappings between the credentials for a user in Active Directory and their corresponding RACF credentials.  
  
 The SSO database is the SQL Server database that stores the information about the affiliate applications, as well as all the encrypted user credentials to all the affiliate applications.  
  
 The master secret server is the Enterprise Single Sign-On server that stores the master secret. All other Single Sign-On servers in the system get the master secret from the master secret server.  
  
 The SSO system also contains one or more SSO Servers. These servers do the mapping between the Windows and back-end credentials, look up the credentials in the SSO database, and administrators use them to maintain the SSO system.  
  
> [!NOTE]
>  You can have only one master secret server and only one SSO database in your SSO system. The SSO database can be remote to the master secret server.  
  
## In This Section  
  
-   [SSO User Groups](../core/sso-user-groups.md)  
  
-   [SSO Components](../core/sso-components.md)  
  
-   [SSO Server](../core/sso-server.md)  
  
-   [Master Secret Server](../core/master-secret-server.md)  
  
-   [SSO Affiliate Applications](../core/sso-affiliate-applications.md)  
  
-   [SSO Mappings](../core/sso-mappings.md)  
  
-   [SSO Tickets](../core/sso-tickets.md)  
  
-   [Configuring SSO](../core/configuring-sso.md)
