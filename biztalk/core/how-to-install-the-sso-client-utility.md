---
title: "How to Install the SSO Client Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, SSO"
  - "SSO, client utility"
  - "client utility [SSO]"
  - "SSO, installing"
ms.assetid: e14d257e-2fde-46af-b90c-5dbc0884536b
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the SSO Client Utility
The stand-alone SSO client utility (command-line utility and user interface-based) allows end users to configure their client mappings in the SSO database. You can install the client utility from a self-extracting file (SSOClientInstall.exe) which is installed with the SSO administration feature. Administrators can also make the installer package available to client users by placing a copy of the installer package on a network share.  
  
 To install the SSO client utility, you must be running one of the following operating systems on the client computer:  
  
- [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
- [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] or [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] (only necessary if you are using the UI-based SSO Client Utility or for leveraging the managed interoperability component of Enterprise SSO).  
  
  After installing the SSO Client Utility, you can launch it from the **Start** menu by clicking **Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Client Utility**.  
  
### To install the SSO client utility  
  
1.  Double-click the installer package SSOClientInstall.  
  
    > [!NOTE]
    >  Ask your Enterprise Single Sign-On Administrator for the location of this file in your enterprise.  
  
     The **WinZip Self-Extractor** program appears.  
  
2.  Select the folder where you want to unzip the files, and click **Unzip**.  
  
     It is recommended to unzip the files in a temporary folder.  
  
     The **Enterprise Single Sign-On Client Setup** program appears.  
  
3.  On **the Welcome to the Enterprise Single Sign-On Client** page, click **Next**.  
  
4.  On the License Agreement page, click **I accept the terms of this license agreement**, and then click **Next**.  
  
5.  On the **User Information** page, type your user name, organization name, and then click **Next**.  
  
6.  On the **Start Installation** page, click **Install**.  
  
7.  On the **Completing the Enterprise Single Sign-On Client Wizard** page, click **Finish**.  
  
8.  Specify the SSO server by doing either of the following:  
  
    -   Open the ENTSSO Administration MMC Snap-In. The **Select SSO Server** dialog will appear. Enter or browse to the SSO Server that you want to connect to when you perform administration operations. To specify the SSO Server for all users on the machine, select **Set SSO Server for all users**.  
  
         OR  
  
    -   At a command prompt, type `ssomanage –server` to specify the SSO server desired. You can also type `ssomanage -serverall` to specify the SSO server that all users of this computer will connect to when performing administration operations.  
  
## See Also  
 [How to Install the SSO Administration Component](../core/how-to-install-the-sso-administration-component.md)   
 [Configuring SSO](../core/configuring-sso.md)   
 [Installing SSO](../core/installing-sso.md)