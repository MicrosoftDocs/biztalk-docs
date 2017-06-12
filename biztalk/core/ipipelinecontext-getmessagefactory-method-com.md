---
title: "IPipelineContext.GetMessageFactory Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80eb1e7d-6f3e-475d-8d68-d3cbec03cd21
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IPipelineContext.GetMessageFactory Method (COM)
Get access to the helper interface to work with BizTalk Server message objects.  
  
## Syntax  
  
```cpp  
  
HRESULT IPipelineContext::GetMessageFactory(  
IBaseMessageFactory**  
ppRet  
);  
  
```  
  
```vb  
  
Function GetMessageFactory() As IBaseMessageFactory  
  
```  
  
#### Parameters  
 *ppRet*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessageFactory** object/interface.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the [IBaseMessageFactory Interface (COM)](../core/ibasemessagefactory-interface-com.md) associated with the pipeline context.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IPipelineContext Interface (COM)](../core/ipipelinecontext-interface-com.md)  
 [IPipelineContext Members (COM)](../core/ipipelinecontext-members-com.md)