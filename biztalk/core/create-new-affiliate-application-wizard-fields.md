---
title: "Create New Affiliate Application Wizard: Fields | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.esso.newapp.wizard.fields"
ms.assetid: 7f9a8675-dd4f-4718-90f1-9538661f7494
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create New Affiliate Application Wizard: Fields
Specify fields for the new Affiliate Application.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Number of fields**|Determines the number of fields that users must provide to connect to the affiliate application.<br /><br /> You can enter as many fields as there are credentials for the affiliate application, but the first field must be the external user ID.|  
|**Masked**|Determines whether this field is masked (that is, whether the characters that the user types are displayed on the screen).<br /><br /> You cannot change this property after you create the application.|  
|**Synchronized**|Determines whether this field is synchronized (used with password synchronization). Only one field can be marked as synchronized.<br /><br /> You cannot change this property after you create the application.|  
|**Credentials are Windows credentials**|Increases security by identifying credentials as Windows credentials; applies to individual applications only.|  
|**Credentials are restricted**|Applies only to group applications. This option is only necessary when using Enterprise Single Sign-On with Microsoft Office 2007.|  
  
## See Also  
 [Implementing Enterprise Single Sign-On](../core/implementing-enterprise-single-sign-on.md)