---
title: "IAssemblerComponent.AddDocument Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f97bcd79-a576-44be-ac05-c088fa3936c7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IAssemblerComponent.AddDocument Method (COM)
Adds the document to the list of messages that are included in an interchange.  
  
## Syntax  
  
```cpp  
  
        HRESULT IAssemblerComponent::AddDocument(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg);  
```  
  
```vb  
  
        Sub AddDocument(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage)  
```  
  
#### Parameters  
 *pContext*  
 [in] Reference to a [IPipelineContext](../core/ipipelinecontext-interface-com.md) object/interface that contains the current pipeline context.  
  
 *pContext*  
 [IPipelineContext](../core/ipipelinecontext-interface-com.md) object/interface that contains the current pipeline context.  
  
 *pInMsg*  
 [in] Reference to a [IBaseMessage](../core/ibasemessage-interface-com.md) object/interface that contains the document to be added to the message set.  
  
 *pInMsg*  
 [IBaseMessage](../core/ibasemessage-interface-com.md) object/interface that contains the document to be added to the message set.  
  
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
 [IAssemblerComponent Interface (COM)](../core/iassemblercomponent-interface-com.md)