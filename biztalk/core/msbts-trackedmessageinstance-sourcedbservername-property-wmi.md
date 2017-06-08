---
title: "MSBTS_TrackedMessageInstance.SourceDBServerName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8325e1d9-a97c-4bc5-8e4f-5a872371c4a1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance.SourceDBServerName Property (WMI)
Contains the name of the SQL Server where the tracked message is stored, either the MessageBox or Archived database.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string SourceDBServerName;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **MessageInstanceID** and **SourceDBName**, this key forms a compound key for the class.  
  
 The maximum value for this property is 80 characters.  
  
 For sample code illustrating the **MSBTS_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](../core/saving-a-message-to-a-file-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.