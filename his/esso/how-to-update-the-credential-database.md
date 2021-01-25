---
description: "Learn more about: How to Update the Credential Database"
title: "How to Update the Credential Database | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0295908f-ad5a-4b12-8b02-7e9d6df56aaf
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Update the Credential Database
You use the commands described here to change the global information in the Credential database, such as the master secret server identification, the account names, auditing in the database, ticket time-out, credential cache time-out, and so on.  
  
## Changing Time-outs for the SSO System  
 You can modify two time-outs at the Enterprise Single Sign-On (SSO) system level:  
  
 **Ticket timeout** **.** This property specifies the length of time for which a ticket that SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket time-out is two minutes. The SSO administrator can change this based on the application requirements.  
  
 **Credential Cache timeout.** This property specifies the credential cache time-out for all SSO servers. SSO servers cache the credentials after the first lookup. By default, the credential cache time-out is 60 minutes. The SSO administrator can change this to an appropriate value based on the security requirements.  
  
 You change both of these time-outs by updating the Credential database.  
  
 The following is an example XML file for updating the Credential database:  
  
```  
<sso>  
<globalnfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### To change time-outs using the Microsoft Management Console (MMC) Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  On the **SSO System Properties** dialog box, click the **General** tab.  
  
5.  Enter the appropriate settings, and then click **OK**.  
  
#### To update the SSO database using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Update**.  
  
#### To update the Credential database using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –updatedb <update file>`, where *\<update file>* is the path and name of the file.  
  
## See Also  
 [How to Configure the Enterprise Single Sign-On Tickets](../esso/how-to-configure-the-enterprise-single-sign-on-tickets.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)
