---
title: "Create New Affiliate Application Wizard: General | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.esso.newapp.wizard.general"
ms.assetid: cfed85cd-794a-460e-a75b-88799656b005
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create New Affiliate Application Wizard: General
Specify general properties for the new Affiliate Application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Application type**|Enterprise Single Sign-On (SSO) defines several different application types. The different application types support different types of mappings between the Windows account and the account on the non-Windows system.<br /><br /> The application types are:<br /><br /> **Individual**: Individual applications support one-to-one mappings between the Windows account and the non-Windows account. In an Individual type application, one Windows account is mapped to one, and only one, non-Windows account. The mapping can be used in either direction, from Windows to non-Windows, or from non-Windows to Windows, or both, depending on the flags that have been set for this application. Thus, Individual applications may be used for Windows initiated SSO, Host initiated SSO, or both.<br /><br /> **Group**:Group applications support mappings between one or more Windows groups or users to one single non-Windows account. The Application Users account is used to define the Windows groups or users that will be used for this Group application.<br /><br /> **Host Group**: Host Group applications are conceptually the reverse of Group applications. They support mappings between a defined group of non-Windows accounts to a single Windows account. The single Windows account that will be used by the non-Windows accounts is defined by the Application Users account for the application. The group of non-Windows accounts that is allowed to access this application is defined by creating a mapping for each non-Windows account. Host Group applications may only be used for Host initiated SSO.|  
|**Application name**|Name of the affiliate application. You cannot change this property after you create the affiliate application.|  
|**Description**|Brief description of the affiliate application.|  
|**Contact information**|The main contact for this affiliate application that users can use. (Can be an e-mail address.)|  
|**Allow local accounts for access accounts**|Determines whether you allow the use of local groups and accounts in the SSO system. You should only select this option in single-computer scenarios.|  
|**Use SSO Affiliate Admin Accounts for Application Admin accounts**|Determines whether the Application Admin Accounts will be the same as the SSO Affiliate Admin Accounts. Default is not selected.|  
  
## See Also  
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)