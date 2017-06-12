---
title: "MSBTS_TrackedMessageInstance.SourceDBName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e73e986-c287-41be-84b6-9287c5acbd91
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance.SourceDBName Property (WMI)
Contains the name of the SQL database where the tracked message is stored, either the MessageBox or Archived database.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string SourceDBName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MessageInstanceID** and **SourceDBServerName**,this key forms a compound key for the class.  
  
 The maximum length for this property is 123 characters.  
  
 For sample code illustrating the **MSBTS_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](../core/saving-a-message-to-a-file-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.