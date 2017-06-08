---
title: "IAssemblerComponent.Assemble Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe93cd74-5ddc-45b4-9427-f6380134453a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IAssemblerComponent.Assemble Method (COM)
Builds an interchange from the messages that were added by the [AddDocument](../core/iassemblercomponent-adddocument-method-com.md) method.  
  
## Syntax  
  
```cpp  
  
        HRESULT IAssemblerComponent::Assemble(  
        IPipelineContext*  
        pContext,  
IBaseMessage**ppOutMsg);  
```  
  
```vb  
  
Function Assemble(  
pContext  
 As IPipelineContext  
) As IBaseMessage  
  
```  
  
#### Parameters  
 *pContext*  
 [in] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pContext*  
 **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *ppOutMsg*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the assembled document.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns an **IBaseMessage** that contains the assembled document.  
  
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
 [IAssemblerComponent Methods (COM)](../core/iassemblercomponent-methods-com.md)   
 [IAssemblerComponent Interface (COM)](../core/iassemblercomponent-interface-com.md)