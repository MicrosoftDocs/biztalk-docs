---
title: "How to Audit SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [SSO], auditing"
  - "SSO, auditing"
  - "auditing [SSO]"
  - "SSO database, auditing"
ms.assetid: dc6d0726-fc31-4af2-9a23-8df9e3fc5836
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Audit SSO
You can use the MMC Snap-In or the command line to set both the positive and negative auditing levels. Results of the auditing are stored in both the event logs and the audit logs of the database.  
  
 SSO administrators can set the positive and negative audit levels that suit their corporate policies. You can set positive and negative audits to one of the following levels:  
  
 0 = None  
  
 1 = Low  
  
 2 = Medium  
  
 3 = High. This level issues as many audit messages as possible.  
  
 The default value for positive auditing is 0 (none), and the default value for negative auditing is 1(low).  
  
 To change the database level auditing, you must update the SSO database using an XML file. A sample XML file for updating the SSO database is:  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### To audit Single Sign-On using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  On the  **System Properties** dialog box, click the **Audits** tab.  
  
5.  Enter the appropriate settings, and click **OK**.  
  
### To audit Single Sign-On using the command line  
  
1.  On the **Start** menu, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig –auditlevel \<positive\>\<negative\>**, where **\<positive\>** is the level of auditing when actions succeed, and **\<negative\>** is the level of auditing when actions fail.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To audit the SSO database  
  
1. Click **Start**, click **Run**, and then type **cmd**.  
  
2. At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –updatedb \<update file\>**, where <strong>\<update file\></strong>is the path and name of the file.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Update the SSO Database](../core/how-to-update-the-sso-database.md)   
 [Using SSO](../core/using-sso.md)