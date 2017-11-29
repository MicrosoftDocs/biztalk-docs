---
title: "Specifying Single Sign-On Administrators and Affiliate Administrators Accounts | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 043d9506-2449-4885-86a9-c2da97914924
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Specifying Single Sign-On Administrators and Affiliate Administrators Accounts
The Enterprise Single Sign-On (SSO) Administrators and Affiliate Administrators accounts can be host group or individual accounts. You must create these accounts before you configure the SSO system. When you are using domain accounts, you must create the SSO Administrators and SSO Affiliate Administrators accounts as domain global security groups in the domain controller. You must be a domain administrator to create these accounts.  
  
 You must specify the Single Sign-On Administrators and Affiliate Administrators accounts in the Credential database. The following example shows XML code that can be used to update  the Credential database:  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  The Configuration Wizard automatically specifies the SSO Administrator and SSO Affiliate Administrator groups in the Credential database.  
  
 Before you update the Credential database with the SSO Administrators group, you must disable the Single Sign-On system. You can use the Microsoft Management Console (MMC) Snap-In or the command line to do this.  
  
### To disable the Enterprise Single Sign-On system using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Disable**.  
  
### To disable the Enterprise Single Sign-On system using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –disablesso`.  
  
### To update the SSO database using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Update**.  
  
### To update the Credential database using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –updatedb <update file>`, where *\<update file>* is the path and name of the XML file.  
  
### To enable the Enterprise Single Sign-On system using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Enable**.  
  
### To enable the Enterprise Single Sign-On system using the command line  
  
1.  Click **Start**, click **Run**, and then type `cmd`.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory.  
  
     The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –enablesso`.  
  
## See Also  
 [Enterprise Single Sign-On User Groups](../esso/enterprise-single-sign-on-user-groups.md)   
 [Enterprise Single Sign-On Tasks](../esso/enterprise-single-sign-on-tasks.md)