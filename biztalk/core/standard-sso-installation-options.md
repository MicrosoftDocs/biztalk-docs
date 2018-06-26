---
title: "Standard SSO Installation Options | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, SSO"
  - "SSO, installing"
ms.assetid: 59aeb503-f369-4145-8a3c-ab60e9ed31a8
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Standard SSO Installation Options
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] leverages the Enterprise Single Sign-On (SSO) capabilities for securely storing credentials to enable single sign-on scenarios.  
  
 BizTalk Server also uses SSO to store custom configuration data of Adapters securely. To do this, BizTalk Server runtime and administration features install SSO as a dependent feature. The default installation of BizTalk Server installs Enterprise SSO.  
  
> [!NOTE]
>  When Enterprise Single Sign-on (Server component) is installed, configuration needs to be performed. The first step to set up an SSO System is to configure the master secret server. It is recommended to set up a stand-alone master secret server. This can be done by only selecting Enterprise Single Sign-on from the custom feature tree in BizTalk Server setup.  
>   
>  We also recommend that any computer running Enterprise Single Sign-On have a time synchronization service running. This keeps the computer time in sync with the rest of the system, which is necessary for SSO ticketing services to function properly.  
  
 **List of installation options**: Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup program. Select **Custom Installation**, and then select the appropriate option from the following list:  
  
- **Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.  
  
- **Enterprise Single Sign-On Master Secret Server ―** Acts as the Master Secret Server in the SSO System. This is the first server in the SSO System that needs to deployed and this allows you to create the SSO database.  
  
  You can also add the following after setup, by using the Add or Remove Programs utility:  
  
- **Server Runtime ―** Core services to enable single sign-on and to store/access configuration data securely.  
  
- **Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On Services.  
  
- **Enterprise Single Sign-On Services with Password Synchronization ―** Services to enable the Password Synchronization feature in the Enterprise SSO System. These services also integrate with the Microsoft Password Change Notification Service. Once you have installed the core Enterprise Single Sign-On services, you can install the Password Synchronization feature of Enterprise SSO from the BizTalk Server package by launching the \Platform\SSO\Setup.exe and selecting the Password Synchronization feature.  
  
- **Software Development Kit** Programming and Reference information.  
  
## In This Section  
  
-   [How to Install the SSO Administration Component](../core/how-to-install-the-sso-administration-component.md)  
  
-   [How to Install the SSO Client Utility](../core/how-to-install-the-sso-client-utility.md)