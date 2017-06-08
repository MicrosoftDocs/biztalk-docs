---
title: "IPipelineContext.StageID Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e89b583d-3d50-499c-b1e2-f046ab330704
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.StageID Property (COM)
Gets the ID of the stage in the pipeline.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::get_StageID(  
GUID*  
StageID  
);  
  
```  
  
```vb  
  
Property StageID() As GUID  
```  
  
#### Parameters  
 *StageID*  
 [out,retval] Globally unique identifier (GUID) used to return the stage ID.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The property was successfully obtained or written.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IPipelineContext Interface (COM)](../core/ipipelinecontext-interface-com.md)   
 [IPipelineContext Members (COM)](../core/ipipelinecontext-members-com.md)