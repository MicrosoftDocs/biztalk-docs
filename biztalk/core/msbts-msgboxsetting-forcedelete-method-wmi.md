---
title: "MSBTS_MsgBoxSetting.ForceDelete Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7399c9ff-ef94-44b7-973d-a183d63109d2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_MsgBoxSetting.ForceDelete Method (WMI)
Deletes the MessageBox object.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
uint32 ForceDelete();  
```  
  
## Remarks  
 This operation bypasses all delete constraints and will succeed even if incomplete instances are still running or are suspended in this MessageBox.  
  
 For more information about the minimum security user rights required to administer the MessageBox database, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.