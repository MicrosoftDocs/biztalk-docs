---
description: "Learn more about: Programming Single Sign-On Overview"
title: "Programming Single Sign-On Overview | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a8de809-0f5f-41e1-b8bd-f2d079b2a41a
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Programming Single Sign-On Overview
A business process that relies on several different applications is likely to face the challenge of dealing with several different security domains. Accessing an application on a Microsoft Windows operating system might require one set of security credentials, whereas accessing an application on an IBM mainframe might require different credentials. Dealing with this profusion of credentials is hard for users, and it can pose an even greater challenge for automating processes. To address this problem, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes Enterprise Single Sign-On (SSO). SSO lets you map a Windows user ID to non-Windows user credentials. This service can simplify business processes that use applications on diverse systems.  
  
 To use SSO, an administrator defines affiliated applications, each of which represents a non-Windows system or application. An affiliated application might be a Customer Information Control System (CICS) application that is running on an IBM mainframe, an SAP ERP system that is running on UNIX, or any other kind of software. Each of these applications has its own mechanism for authentication, and so each requires its own unique credentials.  
  
 SSO stores an encrypted mapping between the Windows user ID of a user and the associated credentials for one or more affiliated applications. These linked pairs are stored in an SSO database. SSO uses the SSO database in two ways. The first way, called *Windows-initiated Single Sign-On*, uses the user ID to determine to which affiliated applications the user has access. For example, a Windows user account might be linked with credentials that grant access to a DB2 database running on a remote AS/400 server. The second way, called *host-initiated Single Sign-On*, acts in reverse: determining what remote applications have access to a specified user ID, and the privileges that go with that account. For example, a remote application might be linked with credentials that grant access to a user account that has administration privileges on a Windows network.  
  
 Note that SSO also includes administration tools to perform various operations. All operations performed on the SSO database are audited; for example, tools are provided that enable an administrator to monitor these operations and set various audit levels. Other tools enable an administrator to disable a particular affiliated application, turn on and off an individual mapping for a user, and perform other functions. There is also a client program that enables end users to configure their own credentials and mappings.  
  
 One of the administrative requirements for Single Sign-On is that your local system must know about the credentials that are required to log on to a remote system. Similarly, the remote system must know about the credentials on your local system. Therefore, when you update your credentials, such as when you update your password on your local computer, you must also inform the remote systems that you have done so. The component you design that synchronizes passwords across an enterprise is called a *password sync adapter*.  
  
## In This Section  
 [Single Sign-On Interface](../esso/single-sign-on-interface.md)  
  
 [Single Sign-On Applications](../esso/single-sign-on-applications.md)  
  
 [What You Should Know Before Programming Single Sign-On](../esso/what-you-should-know-before-programming-single-sign-on.md)  
  
 [Supported Platforms for Single Sign-On](../esso/supported-platforms-for-single-sign-on.md)
