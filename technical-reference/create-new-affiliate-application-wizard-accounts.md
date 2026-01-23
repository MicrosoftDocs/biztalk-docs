---
description: "Learn more about: Create New Affiliate Application Wizard: Accounts"
title: 'Create New Affiliate Application Wizard: Accounts'
TOCTitle: 'Create New Affiliate Application Wizard: Accounts'
ms:assetid: 844c4f3f-50fc-4751-a7d0-65f59d876059
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561149(v=BTS.80)
ms:contentKeyID: 51529374
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.newapp.wizard.accounts
ms.topic: concept-article
---

# Create New Affiliate Application Wizard: Accounts

 

Specify the access accounts for the new Affiliate Application. You can specify one or more accounts for both Application Administrators and Application Users.


> [!NOTE]
> <P>In certain Workgroup environments, clicking the <STRONG>Browse</STRONG> button will cause this screen to close. Instead of using the <STRONG>Browse</STRONG> button, simply type the name of the required accounts in the box.</P>



For group type Affiliate Applications, it is important to note that when specifying multiple accounts for Application Users, the way in which the accounts are ordered is very important. This is because different ordering of accounts can result in different credentials being returned, which could potentially result in an authentication failure.

For example, UserA could be a member of two groups: Group1 and Group2. Each of these groups could in turn be mapped to an account as follows:

  - Group1 is mapped to ExternalCredentials1

  - Group2 is mapped to ExternalCredentials2

If the order specified for 'Application Users' is Group1;Group2, then when the credentials are requested for UserA, SSO returns ExternalCredentials1.

However, if the order specified for 'Application Users' is Group2;Group1, then SSO returns ExternalCredentials2.

**Application Administrators**  
The Windows account(s) that will manage this Affiliate Application.

**Application Users**  
The Windows account(s) for which mappings can be created.

## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

