---
title: "How to Specify SSO Administrators and Affiliate Administrators Accounts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "administrator accounts, SSO"
  - "enabling, SSO"
  - "SSO, enabling"
  - "disabling, SSO"
  - "SSO, disabling"
  - "managing [SSO], configuring administrator accounts"
  - "managing [SSO], enabling"
  - "managing [SSO], disabling"
  - "SSO, administrator accounts"
ms.assetid: 6c300e09-b781-45de-b2da-b1083164a1c0
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Specify SSO Administrators and Affiliate Administrators Accounts
The Enterprise Single Sign-On (SSO) Administrators and Affiliate Administrators accounts can be host group or individual accounts. You must create these accounts before you configure the SSO system.  
  
 When using domain accounts, you must create the SSO Administrators and SSO Affiliate Administrators accounts as a domain global security groups in the domain controller. The domain administrator must create these accounts.  
  
 You must specify the Single Sign-On Administrators and Affiliate Administrators accounts in the SSO database. You must disable the Single Sign-On system before you update the SSO database with the SSO Administrators group.  
  
 The following XML code shows a sample XML for updating the SSO database:  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  The Configuration Wizard automatically specifies the SSO administrator and SSO affiliate administrator groups in the SSO database.  
  
> [!NOTE]
>  If SSO does not configure, users should check whether Domain Local Accounts are being used in a mixed-mode domain.  
  
### To disable the Enterprise Single Sign-On system using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Disable**.  
  
### To disable the Enterprise Single Sign-On system using the command line  
  
1.  On the **Start** menu, click **run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage** –**disablesso**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To update the SSO database using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Update**.  
  
### To update the SSO database using the command line  
  
1. On the **Start** menu, click **run**, and then type **cmd**.  
  
2. At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3. Type **ssomanage –updatedb *\<update file\>**<em>, where *\<update file\></em> is the path and name of the XML file.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
### To enable the Enterprise Single Sign-On system using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Enable**.  
  
### To enable the Enterprise Single Sign-On system using the command line  
  
1.  On the **Start** menu, click **run**, and then type **cmd**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –enablesso**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [SSO User Groups](../core/sso-user-groups.md)