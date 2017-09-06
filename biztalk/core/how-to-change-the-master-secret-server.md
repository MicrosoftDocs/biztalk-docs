---
title: "How to Change the Master Secret Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Master Secret server, promoting"
  - "managing [Master Secret server], promoting servers"
  - "managing [SSO], promoting servers"
  - "SSO, Master Secret server"
  - "modifying, Master Secret server"
  - "Master Secret server, changing"
ms.assetid: 44a786ca-4645-44a8-b33e-d0019f0aeca9
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Change the Master Secret Server
After you set up the master secret server and configure the SSO database, you can change the master secret server if the original master secret server fails and cannot be recovered. To change the master secret server, you need to promote an SSO server to become the master secret server.  
  
### To change the Master Secret Server using the MMC Snap-in  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane, right click **System**, and then click **Properties**. The Master secret server is displayed on the **General** tab of the **System Properties** dialog box.  
  
3.  Click **Change** to select a new Master secret server.  
  
    > [!IMPORTANT]
    >  When using the MMC Snap-in to change the Master Secret Server, the operation must be performed on the Master Secret Server. It is not possible to change the Master Secret Server using the MMC Snap-in from a computer that is not the Master Secret Server.  
  
4.  Logon to the new Master secret server to restore the Master secret to the registry of the new Master secret server.  
  
5.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
6.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
7.  Restart the new Master Secret Server.  
  
8.  Type **ssoconfig –restoreSecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.  
  
     The master secret is stored in the registry at the following location:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To promote a Single Sign-On Server to master secret server using the command line  
  
1.  Create an XML file that includes the name of the SSO server you want to promote to master secret server. For example,  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
    > [!IMPORTANT]
    >  To change the Master Secret Server from a computer that is not the Master Secret Server make sure that the specified XML file contains only the Master Secret Server name. Specifically, it should not contain the SSO Administrators XML tag or the **ssomanage -updatedb** operation will fail.  
  
2.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
3.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage –updatedb** \<**update file**>, where \<**update file**> is the name of the XML file you create in step 1.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
5.  Restart the Master Secret Server.  
  
6.  Type **ssoconfig –restoresecret \<restore file>**, where **\<restore file>** is the path and name of the file where the master secret is stored.  
  
     The master secret is stored in the registry at the following location:  
  
     HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Master Secret Server](../core/master-secret-server.md)   
 [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md)   
 [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)   
 [Using SSO](../core/using-sso.md)