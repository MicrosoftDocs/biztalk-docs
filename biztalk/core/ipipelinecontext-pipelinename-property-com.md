---
title: "IPipelineContext.PipelineName Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7906a2c-1c25-4a08-9b0a-a0900fac7e38
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.PipelineName Property (COM)
Gets the name of the pipeline.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::get_PipelineName(  
BSTR*  
PipelineName  
);  
  
```  
  
```vb  
  
Property PipelineName() As String  
  
```  
  
#### Parameters  
 *ResourceTracker*  
 [out,retval] IResourceTracker used to return the objects being executed.  
  
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