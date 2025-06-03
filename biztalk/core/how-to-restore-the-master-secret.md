---
description: "Learn more about: How to Restore the Master Secret"
title: "How to Restore the Master Secret"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Restore the Master Secret
As part of data recovery procedures, you may need to restore the master secret to re-use existing data. In order to perform this task, you must log on to the master secret server with an account that is both a Windows administrator and an SSO administrator.  
  
### To restore the master secret using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Restore Secret**.  
  
### To restore the master secret using the command line  
  
1.  On the **Start** menu, click **All Programs**, and then click **Accessories**. Right-click **Command Prompt**, and then click **Run As…**.  
  
2.  Select the appropriate Administrator, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig –restoreSecret \<restore file\>**, where **\<restore file\>** is the path and name of the file where the master secret is stored.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md)   
 [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md)   
 [Master Secret Server](../core/master-secret-server.md)   
 [Managing the Master Secret](../core/managing-the-master-secret.md)
