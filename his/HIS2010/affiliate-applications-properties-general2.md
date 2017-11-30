---
title: "Affiliate Applications Properties: General2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts06.esso.affapp.properties.general"
ms.assetid: 65a77b54-7cf1-4360-9785-97bdfbd0e113
caps.latest.revision: 4
---
# Affiliate Applications Properties: General
Use this dialog box to view or change general properties for the affiliate application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application type**|Enterprise Single Sign-On (SSO) defines several different application types. The different application types support different types of mappings between the Windows account and the account on the non-Windows system.<br /><br /> The application types are:<br /><br /> **Individual**: Individual applications support one-to-one mappings between the Windows account and the non-Windows account. In an Individual type application, one Windows account is mapped to one, and only one, non-Windows account. The mapping can be used in either direction, from Windows to non-Windows, or from non-Windows to Windows, or both, depending on the flags that have been set for this application. Thus, Individual applications may be used for Windows initiated SSO, Host initiated SSO, or both.<br /><br /> **Group**: Group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.<br /><br /> You can also specify multiple accounts for the SSO Application Users role. Each account that you specify can be associated with an external account.<br /><br /> For example, it is possible to map a domain user (domain\userA) to one set of external credentials (ExternalUser1). The same domain\userA could also be a member of Domain Group (domain\group1) and this group could be mapped to a different set of external credentials (ExternalUser2). In this case, it is important that the administrator (who must be an Application Administrator or above) specifies the correct order for the Application Users accounts.<br /><br /> The mapping for the first account (in the Order) of which the caller is a member is the one that will be used. In this case, if mapping for domain\userA to ExternalUser1 is set to Order 0, SSO will return this set of credentials for domain\UserA.<br /><br /> Only an application administrator, SSO affiliate administrator, or SSO administrator can create a group mapping.<br /><br /> You cannot specify the same group application for Windows-initiated SSO and Host-initiated SSO.<br /><br /> **Host Group**: Host Group applications are conceptually the reverse of Group applications. They support mappings between a defined group of non-Windows accounts to a single Windows account. The single Windows account that will be used by the non-Windows accounts is defined by the Application Users account for the application. The group of non-Windows accounts that is allowed to access this application is defined by creating a mapping for each non-Windows account. Host Group applications may only be used for Host initiated SSO. **Important:**  Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped. **Important:**  When you use group mappings, the members of the group can obtain the credential information for the group mapping.|  
|**Application name**|Name of the affiliate application. You cannot change this property after you create the affiliate application.|  
|**Description**|Brief description of the affiliate application.|  
|**Contact information**|The main contact for this affiliate application that users can use. (Can be an e-mail address.)|  
|**Allow local accounts for access accounts**|Determines whether you allow the use of local groups and accounts in the SSO system. You should select this option only in single-computer scenarios.|  
|**Use SSO Affiliate Admin Accounts for Application Admin accounts**|Determines whether the Application Admin accounts will be the same as the SSO Affiliate Admin accounts. Default is not selected.|  
  
## See Also  
 [Enterprise Single Sign-On (Configuration)](../HIS2010/enterprise-single-sign-on-configuration-2.md)   
 [Affiliate Applications Properties](../HIS2010/affiliate-applications-properties1.md)