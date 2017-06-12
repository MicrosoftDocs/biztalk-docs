---
title: "Group Properties Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.admin.group.properties"
ms.assetid: 0e9524fe-5a9b-44c6-bfc6-e0656848483b
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Group Properties Dialog Box
Use the **Group Properties** window to view or modify BizTalk Group properties.  
  
## General Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Name**|Type the group name. The name in this box appears next to the **Group** node in the Console tree, along with the server name and the management database name.|  
|**Server**|Displays the server on which the management database is physically stored.|  
|**Database**|Displays the management database on which all configuration settings for this group are stored.|  
|**SSO Server name**|Type the name of the Enterprise Single Sign-On server that this computer will use to access the configuration information for the adapters. This is the name of the SSO Server used to connect to the SSO database.|  
|**BizTalk Administrator Group**|Displays the name of the administrators group that has rights to manage the BizTalk Server environment after installation.|  
|**BizTalk Operators Group**|Displays the name of the operators group that has rights to view configuration, run queries, and perform machine maintenance and basic application monitoring.|  
|**BizTalk B2B Operators Group**|Displays the name of the B2B operators group that has rights to view and manage party(Trading Partner) data including EDI/AS2 settings for the parties.|  
|||  
|||  
  
## Databases Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Databases**|Displays the names of all databases in the application and the servers on which they reside, as specified during configuration.|  
  
## Certificate Tab  
  
## UIElement List  
  
|Use this|To do this|  
|--------------|----------------|  
|**Signature certificate - Common Name**|Displays the common name of the selected certificate.|  
|**Signature certificate - Thumbprint**|Displays the thumbprint of the private key certificate that is used to digitally sign outbound messages from this group. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number 0 to 9 or a letter A to F).|  
|**Signature certificate - Remove certificate**|Click to remove the displayed certificate.|  
|**Signature certificate - Browse**|Click to display the **Select Certificate** dialog box, where you select the signature certificate you want to use with the group.|  
  
## See Also  
 [BizTalk Groups](../core/biztalk-groups.md)   
 [How to Add a Server to a Group](../core/how-to-add-a-server-to-a-group.md)   
 [How to Remove a Server from a Group](../core/how-to-remove-a-server-from-a-group.md)   
 [Managing Groups](../core/managing-groups.md)   
 [How to Modify Group Properties](../core/how-to-modify-group-properties.md)   
 [How to Export Bindings for a BizTalk Group](../core/how-to-export-bindings-for-a-biztalk-group.md)   
 [How to Move a Server from One Group to Another](../core/how-to-move-a-server-from-one-group-to-another.md)