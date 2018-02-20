---
title: "How to Change the Master Secret Server | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8cfd3a5-e7a6-4d97-9661-9c8d49a0b6f0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Change the Master Secret Server
After you set up the master secret server and configure the Credential database, you can change the master secret server if the original master secret server fails and cannot be recovered. To change the master secret server, you must promote a Single Sign-On (SSO) server to become the master secret server.  
  
### To change the master secret server using the MMC Snap-in  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane, right-click **System**, and then click **Properties**.  
  
     The master secret server is displayed on the **General** tab of the **SSO System Properties** dialog box.  
  
3.  Click **Change** to select a new master secret server.  
  
### To promote a Single Sign-On server to master secret server  
  
1.  Create an XML file that includes the name of the SSO server that you want to promote to master secret server. For example:  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
2.  Click **Start**, click **Run**, and then type `cmd`.  
  
3.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type `ssomanage –updatedb <update file>`, where \<*update file*> is the name of the XML file that you create in step 1.  
  
5.  Restart the master secret server.  
  
6.  Type `ssoconfig –restoresecret <restore file>`, where *\<restore file>* is the path and name of the file where the master secret is stored.  
  
## See Also  
 [Master Secret Server](../esso/master-secret-server.md)   
 [How to Cluster the Master Secret Server](../esso/how-to-cluster-the-master-secret-server.md)   
 [How to Update the Credential Database](../esso/how-to-update-the-credential-database.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)