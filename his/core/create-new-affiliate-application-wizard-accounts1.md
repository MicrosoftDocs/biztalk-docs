---
title: "Create New Affiliate Application Wizard: Accounts1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.esso.newapp.wizard.accounts"
ms.assetid: d1fe7d59-67e4-495a-82c8-e3b269fbc963
caps.latest.revision: 4
---
# Create New Affiliate Application Wizard: Accounts
Specify the access accounts for the new Affiliate Application. You can specify one or more accounts for both Application Administrators and Application Users.  
  
> [!NOTE]
>  In certain Workgroup environments, clicking the **Browse** button will cause this screen to close. Instead of using the **Browse** button, simply type the name of the required accounts in the box.  
  
 For group type Affiliate Applications, it is important to note that when specifying multiple accounts for Application Users, the way in which the accounts are ordered is very important. This is because different ordering of accounts can result in different credentials being returned, which could potentially result in an authentication failure.  
  
 For example, UserA could be a member of two groups: Group1 and Group2. Each of these groups could in turn be mapped to an account as follows:  
  
-   Group1 is mapped to ExternalCredentials1  
  
-   Group2 is mapped to ExternalCredentials2  
  
 If the order specified for 'Application Users' is Group1;Group2, then when the credentials are requested for UserA, SSO returns ExternalCredentials1.  
  
 However, if the order specified for 'Application Users' is Group2;Group1, then SSO returns ExternalCredentials2.  
  
 **Application Administrators**  
 The Windows account(s) that will manage this Affiliate Application.  
  
 **Application Users**  
 The Windows account(s) for which mappings can be created.  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../core/enterprise-single-sign-on-configuration-2.md)   
 [Create New Affiliate Application Wizard](../core/create-new-affiliate-application-wizard1.md)