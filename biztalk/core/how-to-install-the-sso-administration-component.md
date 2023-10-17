---
title: "Install the SSO Administration Component | Microsoft Docs"
description: Do a custom installation to get SSO Administration, and use ssomanage or SSO administration to enter the server name in BizTalk Server
ms.custom: ""
ms.date: "09/27/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the SSO Administration Component

## Overview
You can install the Enterprise Single Sign-On Administration component as a stand-alone feature. This is useful if you need to administer the SSO system remotely. The hardware and software requirements are the same as for a typical Enterprise SSO Runtime Services installation.  
  
 After installing the administration component, you enter the SSO Server to be used for management. You can do this with either the command line tool (ssomanage.exe), or the SSO Administration MMC Snap-In. Both procedures are listed in this topic.  
  
 Installing the SSO administrative utility (ssomanage.exe) does not create shortcuts on the Start menu to access the command line utilities. To run the SSO administrative utilities after installation, you must open a command prompt, and navigate to the SSO directory at `Program Files\Common Files\Enterprise Single Sign-On`.  
  
 The Enterprise SSO Administration feature also includes an MMC Snap-in. MMC 3.0 must be installed on your computer for the Snap-in to function.  
  
 To open the Enterprise SSO MMC Snap-in from the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.  
  
## Install the Enterprise Single Sign-On administrative component  
  
- Do a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and select only the Enterprise Single Sign-On Administration feature. For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], this is listed under **Additional Software**.  
  
## Enter the server using the MMC Snap-In  
  
1.  After installing the administrative component on a computer where it is not currently installed, open the SSO Administration Snap-In.  
  
     In the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then select **SSO Administration**.  
  
2.  In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.  
  
     The **Select SSO Server** dialog box will appear.  
  
3.  Enter or browse to the SSO server name you want to specify. To specify the SSO server for all users on the computer, select **Set SSO Server for all users**.  
  
4.  Click **OK**.  
  
## Enter the server using the command line tool  
  
1.  Click **Start**, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is `\Program Files\Common Files\Enterprise Single Sign-On`.  
  
3.  Enter the SSO Server by selecting one of the following options:  
  
    1.  Type **ssomanage –server** to enter the SSO Server you want to connect to when performing administration operations.  
  
         \- OR -  
  
    2.  Type **ssomanage -serverall** to enter the SSO Server all users of this computer will connect to when performing administration operations.  
  
## See Also  
 [How to Install the SSO Client Utility](../core/how-to-install-the-sso-client-utility.md)   
 [Configuring SSO](../core/configuring-sso.md)   
 [Installing SSO](../core/installing-sso.md)
