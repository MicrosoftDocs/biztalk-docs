---
title: "How to Install the SSO Administration Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, SSO"
  - "administrative component [SSO]"
  - "SSO, administrative component"
  - "SSO, installing"
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the SSO Administration Component
It is possible to install the Enterprise Single Sign-On Administration component as a stand-alone feature. This is useful if you need to administer the SSO system remotely. The hardware and software requirements are the same as for a typical Enterprise SSO Runtime Services installation.  
  
 After installing the administration component, you will need to specify the SSO Server to be used for management. You can do this with either the command line tool (ssomanage.exe) or the SSO Administration MMC Snap-In. Both procedures are shown below.  
  
 Installing the SSO administrative utility (ssomanage.exe) does not create shortcuts on the Start menu to access the command line utilities. To run the SSO administrative utilities after installation, you must open a command prompt and navigate to the SSO directory located at Program Files\Common Files\Enterprise Single Sign-On.  
  
 The Enterprise SSO Administration feature also includes an MMC Snap-in. The Snap-in is installed on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] and Windows Vista SP2. It is not supported on [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]. You must also have MMC 3.0 installed on your computer for the Snap-in to function.  
  
 To open the Enterprise SSO MMC Snap-in click the **Start** menu, then click **All Programs**, **Microsoft Enterprise Single Sign-On**, and **SSO Administration**.  
  
### To install the Enterprise Single Sign-On administrative component  
  
-   Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], selecting only the Enterprise Single Sign-On Administration feature. For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], this can be found under **Additional Software**.  
  
### To specify the server using the MMC Snap-In  
  
1.  After installing the administrative component on a computer where it is not currently installed, open the SSO Administration Snap-In.  
  
     Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.  
  
     The **Select SSO Server** dialog box will appear.  
  
3.  Enter or browse to the SSO server name you want to specify. To specify the SSO server for all users on the computer, select **Set SSO Server for all users**.  
  
4.  Click **OK**.  
  
### To specify the server using the command line tool  
  
1.  Click **Start**, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Specify the SSO Server by selecting one of the following options:  
  
    1.  Type **ssomanage –server**to specify the SSO Server you want to connect to when performing administration operations.  
  
         \- OR -  
  
    2.  Type **ssomanage -serverall** to specify the SSO Server all users of this computer will connect to when performing administration operations.  
  
## See Also  
 [How to Install the SSO Client Utility](../core/how-to-install-the-sso-client-utility.md)   
 [Configuring SSO](../core/configuring-sso.md)   
 [Installing SSO](../core/installing-sso.md)