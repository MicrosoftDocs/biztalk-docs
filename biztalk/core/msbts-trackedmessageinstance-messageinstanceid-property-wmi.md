---
title: "MSBTS_TrackedMessageInstance.MessageInstanceID Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eec5b1c3-9da1-4018-8c4b-56ceface2e26
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance.MessageInstanceID Property (WMI)
Contains the ID of the message instance.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string MessageInstanceID;  
```  
  
## Remarks  
 This property is read-only.  
  
 This property has a **Key** qualifier. Along with **SourceDBName** and **SourceDBServerName**, this key forms a compound key for the class.  
  
 For sample code illustrating the **MSBTS_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](../core/saving-a-message-to-a-file-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.