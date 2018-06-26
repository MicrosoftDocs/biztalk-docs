---
title: "How to Install the Enterprise Single Sign-On Client Utility | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b517ce65-85c8-419d-851b-cf025d3b0e4e
caps.latest.revision: 6
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Install the Enterprise Single Sign-On Client Utility
The stand-alone Single Sign-On (SSO) client utility (ssoclient.exe) enables end users to configure their client mappings in the credential database. You can install the client utility from a self-extracting file (SSOClientInstall.exe), which is installed with the SSO administration feature. Administrators can also make the installer package available to client users by placing a copy of the installer package on a network share.  
  
 To install the SSO client utility, you must be running one of the following operating systems on the client computer in addition to version 3.51 of the .NET Framework:  
  
- Windows Server 2003 R2 SP2  
  
- Windows Vista SP2  
  
- Windows 7  
  
- Windows Server 2008 SP2  
  
- Windows Server 2008 R2  
  
  Installing the SSO client utility does not create shortcuts on the **Start** menu for you to access the command-line utilities. To run the SSO client utility after installation, you must open a command prompt and navigate to the SSO directory located at Program Files\Common Files\Enterprise Single Sign-On.  
  
### To install the SSO client utility  
  
1.  Double-click the installer package, SSOClientInstall.  
  
    > [!NOTE]
    >  Ask your Enterprise Single Sign-On administrator for the location of this file in your enterprise.  
  
     The WinZip Self-Extractor program appears.  
  
2.  Select the folder where you want to unzip the files, and then click **Unzip**.  
  
     It is recommended that you unzip the files in a temporary folder.  
  
     The **Enterprise Single Sign-On Client Setup** program appears.  
  
3.  On the **Welcome to the Enterprise Single Sign-On Client** page, click **Next**.  
  
4.  On the **License Agreement** page, click **I accept the terms of this license agreement**, and then click **Next**.  
  
5.  On the **User Information** page, type your user name, organization name, and then click **Next**.  
  
6.  On the **Start Installation** page, click **Install**.  
  
7.  On the **Completing the Enterprise Single Sign-On Client Wizard** page, click **Finish**.  
  
8.  Specify the SSO server by doing either of the following:  
  
    -   Type `ssomanage –server` to specify the SSO server that you want to connect to when you perform administration operations. You can also type `ssomanage -serverall` to specify the SSO server that all users of this computer will connect to when performing administration operations.  
  
         OR  
  
    -   Open the ENTSSO Administration MMC Snap-In. The Select SSO Server dialog will appear. Enter or browse to the SSO Server desired. To specify the SSO Server for all users on the machine, select **Set SSO Server for all users**.  
  
## See Also  
 [How to Install the Enterprise Single Sign-On Administration Component](../esso/how-to-install-the-enterprise-single-sign-on-administration-component.md)   
 [Configuring Enterprise Single Sign-On](../esso/configuring-enterprise-single-sign-on1.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)