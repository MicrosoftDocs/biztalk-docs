---
description: "Learn more about: How to Remove Enterprise Single Sign-On"
title: "How to Remove Enterprise Single Sign-On"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Remove Enterprise Single Sign-On
If you remove [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], Enterprise Single Sign-On (SSO) is no longer configured, but it is not removed. You must remove SSO separately. You can also restore configuration information including the master secret to reuse existing data. For more information, see [How to Restore the Master Secret](../esso/how-to-restore-the-master-secret.md).  
  
### To remove Enterprise Single Sign-On  
  
1. Back up the master secret key.  
  
    For more information, see [How to Back Up the Master Secret](../esso/how-to-back-up-the-master-secret.md).  
  
2. Uninstall [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
3. Click **Start**, point to **Settings**, and then click **Control Panel**.  
  
4. Click **Add or Remove Programs**.  
  
5. In **Add or Remove Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **Remove**.  
  
6. Click **Yes** when you are prompted to confirm the removal of Microsoft Enterprise Single Sign-On.  
  
## See Also  
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)
