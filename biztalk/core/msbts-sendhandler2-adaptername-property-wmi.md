---
title: "MSBTS_SendHandler2.AdapterName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30c59145-1eb6-4342-8355-f861058aa5af
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler2.AdapterName Property (WMI)
This property contains the name of the adapter used by the given instance.  This property is required for instance creation.  
  
## Syntax  
  
```  
  
stringAdapterName;  
```  
  
## Remarks  
 This property can be written during instance creation.  After that it is read only.  
  
 The maximum length for this property is 256 characters.  
  
> [!NOTE]
>  The adapter name must be in upper case or the instance will fail.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.