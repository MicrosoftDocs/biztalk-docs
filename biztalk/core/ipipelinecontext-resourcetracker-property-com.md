---
title: "IPipelineContext.ResourceTracker Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 494b8687-6238-4ae2-bd25-d9d6842a4599
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.ResourceTracker Property (COM)
Reports the objects used during execution.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::get_ResourceTracker(  
IResourceTracker*  
PipelineName  
);  
  
```  
  
```vb  
  
Property ResourceTracker() As IResourceTracker  
  
```  
  
#### Parameters  
 *PipelineName*  
 [out,retval] String used to return the pipeline name.  
  
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