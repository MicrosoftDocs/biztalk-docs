---
title: "IDisassemblerComponent.Disassemble Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61ad5f2a-26d8-4f47-89f3-549a267db554
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDisassemblerComponent.Disassemble Method (COM)
Performs the disassembling of an incoming document.  
  
## Syntax  
  
```cpp  
  
        HRESULT IDisassemblerComponent::Disassemble(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg);  
```  
  
```vb  
  
        Sub Disassemble(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage)  
```  
  
#### Parameters  
 *pContext*  
 [in] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pContext*  
 **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pInMsg*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message to be disassembled.  
  
 *pInMsg*  
 **IBaseMessage** object/interface that contains the message to be disassembled.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
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
 [IDisassemblerComponent Interface (COM)](../core/idisassemblercomponent-interface-com.md)   
 [IDisassemblerComponent Members (COM)](../core/idisassemblercomponent-members-com.md)