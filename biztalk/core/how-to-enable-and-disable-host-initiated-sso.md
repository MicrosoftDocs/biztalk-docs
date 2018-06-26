---
title: "How to Enable and Disable Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "host initiated SSO, disabling"
  - "disabling, host initiated SSO"
  - "enabling, host initiated SSO"
  - "host initiated SSO, enabling"
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable and Disable Host Initiated SSO
By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.  
  
### To enable host initiated SSO using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Select the **Enable host initiated SSO** box, and click **OK**.  
  
### To enable host initiated SSO using the command line  
  
1. On the **Start** menu, click **Run**.  
  
2. In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3. At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4. Type **ssomanage -enable hisso**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
   Disabling SSO applies to the entire SSO system, and all operations related to host initiated SSO are turned off.  
  
#### To disable host initiated SSO using the MMC Snap-In  
  
1.  On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Clear the **Enable host initiated SSO** box, and click **OK**.  
  
#### To disable host initiated SSO using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -disable hisso** as appropriate.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Host Initiated SSO](../core/host-initiated-sso.md)