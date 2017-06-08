---
title: "IPipelineContext.StageIndex Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7472420e-217b-4dca-a2a2-a2f78d3df186
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.StageIndex Property (COM)
Gets the index of the pipeline stage where the current component is located.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::get_StageIndex(  
LONG*  
StageIndex  
);  
  
```  
  
```vb  
  
Property StageIndex() As Long  
  
```  
  
#### Parameters  
 *StageIndex*  
 [out,retval] Integer used to return the stage index.  
  
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