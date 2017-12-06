---
title: "Single Sign-On in Transaction Integrator2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ef78e04-731a-409a-ba29-d9628d92f39f
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Single Sign-On in Transaction Integrator
Single Sign-On (SSO) is a mechanism that enables a user to enter a user name and password once to access multiple applications. It gives users simplified logon and maintenance of the many passwords needed to access Windows and back end systems and/or applications. It enables applications to integrate by automating the process of logging on to the host/backend system.  
  
 In general, there are three types of single sign-on services:  
  
-   **Common authentication single sign-on:** These services enable you to connect to multiple applications within your computer. Your credentials are requested and verified once when you log into the computer, and these credentials are used to determine what actions you can perform based on your permissions. An example of this type of single sign-on is Exchange Server, which uses Windows Integrated Security. Once the user has logged on to Windows, they do not need to provide additional credentials to access their e-mail.  
  
-   **Internet single sign-on:** These services enable you to access resources over the Internet by using a single set of user credentials. The user provides a set of credentials to log on to different Web sites that belong to different organizations. An example of this type of single sign-on is Windows Live ID.  
  
-   **Intranet single sign-on:** These services enable you to connect to multiple heterogeneous applications and systems within the enterprise environment in your company. An example of this type of single sign-on is Enterprise Single Sign-On, which provides a framework for Windows applications to integrate with non-Windows applications to enable single sign-on.  
  
 SSO facilitates the translation of credentials by the Security Policy Wizard. SSO lets you define and manage the relationship between foreign host user ID and password credentials to Windows credentials. The basis for managing these relationships is the SSO Affiliated Application.  
  
 An Affiliated Application is a grouping of well defined host user identities under a logical entity that reflects the host administrators view of application processing systems in the non-Windows environments.  
  
 When SSO is handed a set of host credentials (user ID and password) along with a valid SSO Affiliated Application, SSO returns a Windows Access Token that represents the Windows credentials. HIP uses this Access Token when setting up the execution thread for methods on server object.  
  
 To make this process easier, the Security Policy must know which SSO Affiliated Applications are to be queried in an attempt to gain access to the Windows credentials (access token) needed to execute methods on the server object. The wizard pane lets the user select from a list of valid SSO Affiliated Applications and add them to the Security Policy being defined. The wizard pane also lets the user remove SSO Affiliated Applications previously defined to the Security Policy.  
  
## In this Section  
 [SSO with Host-Initiated Processing](../core/sso-with-host-initiated-processing.md)  
  
## See Also  
 [Application Integration (Security)](../core/application-integration-security.md)