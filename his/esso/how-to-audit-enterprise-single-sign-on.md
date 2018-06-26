---
title: "How to Audit Enterprise Single Sign-On | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56670e4e-e2de-4f08-8ccb-d645d7a5a740
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Audit Enterprise Single Sign-On
Use this command to set both the positive and negative auditing levels. Single Sign-On (SSO) administrators can set the positive and negative audit levels that suit their corporate policies. You can set positive and negative audits to one of the following levels:  
  
- 0 = None  
  
- 1 = Low  
  
- 2 = Medium  
  
- 3 = High - This level issues as many audit messages as possible.  
  
  The default value for positive auditing is 0 (none), and the default value for negative auditing is 1(low).  
  
  To change the database-level auditing, you must update the Credential database using an XML file. The following is an example XML file that is used for updating the Credential database:  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### To audit Single Sign-On using the Microsoft Management Console (MMC) Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  In the **SSO System Properties** dialog box, click the **Audits** tab.  
  
5.  Enter the appropriate settings, and then click **OK**.  
  
### To audit Single Sign-On using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssoconfig –auditlevel < positive level>``<negative level>`, where *\<positive level>* is the level of auditing when actions succeed, and *\<negative auditing>* is the level of auditing when actions fail.  
  
### To audit the Credential database  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –updatedb <update file>`, where *\<update file>* is the path and name of the file.  
  
## See Also  
 [How to Update the Credential Database](../esso/how-to-update-the-credential-database.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)