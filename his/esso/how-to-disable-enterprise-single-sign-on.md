---
title: "How to Disable Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aaf86a15-6ede-4fa0-b736-42ed411b4feb
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Disable Enterprise Single Sign-On
The disabling command disables the entire Single Sign-On system.  
  
 There will be a short delay before all Single Sign-On servers are disabled, because they poll the Credential database for the latest global information.  
  
### To disable Enterprise Single Sign-On using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Disable**.  
  
### To disable Enterprise Single Sign-On using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disablesso`.  
  
## See Also  
 [How to Enable Enterprise Single Sign-On](../esso/how-to-enable-enterprise-single-sign-on.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)