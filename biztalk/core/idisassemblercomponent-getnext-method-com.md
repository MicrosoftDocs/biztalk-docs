---
title: "IDisassemblerComponent.GetNext Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d01f6e61-9490-4b52-9772-e16e9c5f5c0a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IDisassemblerComponent.GetNext Method (COM)
Gets the next message from the message set resulting from the disassembler execution.  
  
## Syntax  
  
```cpp  
  
        HRESULT IDisassemblerComponent::GetNext(  
        IPipelineContext*  
        pContext,  
IBaseMessage**ppOutMsg);  
```  
  
```vb  
  
Function GetNext(  
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
 [out,retval] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the next message from the message set. Returns **NULL** if there are no more messages left.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns an [IBaseMessage](../core/ibasemessage-interface-com.md) containing the disassembled document. Returns **NULL** if there are no more messages left.  
  
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