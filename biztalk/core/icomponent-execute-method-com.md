---
title: "IComponent.Execute Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d9bf0db-d6e5-4f68-a78e-a8b25d3a33fc
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IComponent.Execute Method (COM)
Executes a pipeline component to process the input message and get the resulting message.  
  
## Syntax  
  
```cpp  
  
        HRESULT IComponent::Execute(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg,  
IBaseMessage**ppOutMsg);  
```  
  
```vb  
  
        Function Execute(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage) As IBaseMessage  
```  
  
#### Parameters  
 *pContext*  
 [in] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pContext*  
 **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pInMsg*  
 [in] Reference to a **IBaseMessage** object/interface that contains the message to process.  
  
 *pInMsg*  
 **IBaseMessage** object/interface that contains the message to process.  
  
 *ppOutMsg*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessage** object/interface, which will contain the resulting message.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns an **IBaseMessage** that contains the resulting message.  
  
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
 [IComponent Interface (COM)](../core/icomponent-interface-com.md)   
 [IComponent Members (COM)](../core/icomponent-members-com.md)