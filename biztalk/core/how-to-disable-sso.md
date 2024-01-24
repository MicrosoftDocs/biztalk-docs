---
description: "Learn more about: How to Disable SSO"
title: "How to Disable SSO"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Disable SSO
You can disable the entire Single Sign-On system by using either the MMC Snap-In or the command line.  
  
 There will be a short delay for all Single Sign-On Servers to be disabled, as they poll the SSO database for the latest global information.  
  
### To disable Enterprise Single Sign-On using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Disable**.  
  
### To disable Enterprise Single Sign-On using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –disablesso**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Enable SSO](../core/how-to-enable-sso.md)   
 [Using SSO](../core/using-sso.md)
