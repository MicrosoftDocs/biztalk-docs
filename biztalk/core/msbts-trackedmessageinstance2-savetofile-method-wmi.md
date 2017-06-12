---
title: "MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53f35713-c618-463d-abe5-66ff315b706b
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance2.SaveToFile Method (WMI)
This method saves message context and parts into multiple output files.  
  
## Syntax  
  
```  
  
uint32SaveToFile(string OutputFolderFullPath);  
```  
  
#### Parameters  
  
|||  
|-|-|  
|**OutputFolderFullPath**|[in] Describes the full path for the folder that will contain the output files.|  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 The syntax shown is language neutral.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.