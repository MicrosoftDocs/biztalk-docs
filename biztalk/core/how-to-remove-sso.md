---
title: "How to Remove SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Master Secret server, deleting"
  - "SSO, deleting"
  - "deleting, SSO"
  - "deleting, Master Secret server"
ms.assetid: 0e1ad8e3-0938-4f36-b85b-4631d0eeb8c9
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove SSO
If you remove BizTalk Server, Enterprise Single Sign-On (SSO) is no longer configured unless a dependent product is using it. However, it is not removed. You must remove SSO separately. You can also restore configuration information including the master secret to reuse existing data. For more information, see [How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md).  
  
### To remove Enterprise Single Sign-On  
  
1. Back up the master secret key. For more information, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).  
  
2. Uninstall [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3. On the **Start** menu, click **Control Panel**.  
  
4. Click **Add/Remove Programs**.  
  
5. In the **Add/Remove Programs** dialog box, click **Microsoft Enterprise Single Sign-On**, and then click **Remove**.  
  
6. Click **Yes** when prompted to confirm the removal of Microsoft Enterprise Single Sign-On.  
  
   > [!NOTE]
   >  If you have BizTalk Server Runtime, Development, or Administration features installed, or Host Integration Server Administration features installed, you will not be able to uninstall the SSO Runtime or Administration components until all dependencies are removed.  
  
## See Also  
 [Installing SSO](../core/installing-sso.md)