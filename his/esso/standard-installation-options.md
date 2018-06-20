---
title: "Standard Installation Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb3d7d39-39b3-4f8c-a577-67ecde7fd015
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Standard Installation Options
Host Integration Server takes advantage of the Enterprise Single Sign-On (SSO) capabilities for securely storing critical information.  
  
 By default, Enterprise Single Sign-On is not installed with the rest of Host Integration Server. You can install it by using the following procedure.  
  
> [!NOTE]
>  When Enterprise Single Sign-on (Server component) is installed, configuration must be performed. The first step to set up an SSO system is to configure the master secret server. We recommend that you set up a stand-alone master secret server. You can do this by only selecting Enterprise Single Sign-On from the custom feature tree in  Host Integration Server Setup.  
>   
>  We also recommend that any computer that is running Enterprise Single Sign-On have a time synchronization service running. This keeps the computer time in sync with the rest of the system. This is necessary for SSO ticketing services to function correctly.  
  
### To install Enterprise Single Sign-On  
  
1. Run the Setup program again.  
  
2. Select **Custom Installation**, and then select the appropriate option from the following list:  
  
    When you run the HIS Server package, you have the following options:  
  
   - **Enterprise Single Sign-On Master Secret Server ―** Acts as the master secret server in the SSO system. This is the first server in the SSO system that must be deployed. This enables you to create the SSO Credential Database.  
  
   - **Enterprise Single Sign-On Administration ―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On services.  
  
   - **Server Runtime ―** Core services to enable single sign-on and to store/access configuration data securely.  
  
   - **Enterprise Single Sign-On Services with Password Synchronization ―** Services to enable the Password Synchronization feature in the Enterprise SSO system. These services also integrate with the Microsoft Password Change Notification Service. After you have installed the core Enterprise Single Sign-On services, you can install the Password Synchronization feature of Enterprise SSO from the Host Integration Server package by starting Setup (\Platform\SSO\Setup.exe) and selecting the **Password Synchronization** feature.  
  
   - **Enterprise Single Sign-On Services ―** Provides the core services to enable single sign-on and to store/access configuration data securely. It can also act as the master secret server in the SSO system.  
  
   - **Enterprise Single Sign-On Services with Password Synchronization ―** Provides the services to enable the Password Synchronization feature in the Enterprise SSO System. These services also integrate with the Microsoft Password Change Notification Service.  
  
   - **Enterprise Single Sign-On Administration** **―** Administration and client tools for mapping and connecting to Enterprise Single Sign-On services.  
  
     When you run the HIS Client package, you can choose from the following options:  
  
   - **Enterprise Single Sign-On Administration ―** Administration and client tools for managing and connecting to Enterprise Single Sign-On services.  
  
   - **Enterprise Single Sign-On Client ―** Client tools for end users to manage their mappings.  
  
## See Also  
 [How to Install the Enterprise Single Sign-On Administration Component](../esso/how-to-install-the-enterprise-single-sign-on-administration-component.md)   
 [How to Install the Enterprise Single Sign-On Client Utility](../esso/how-to-install-the-enterprise-single-sign-on-client-utility.md)   
 [High-Availability Installation Options](../esso/high-availability-installation-options.md)   
 [How to Remove Enterprise Single Sign-On](../esso/how-to-remove-enterprise-single-sign-on.md)