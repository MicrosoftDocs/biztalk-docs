---
title: "IProbeMessage.Probe Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1fefbfe0-0eb4-4544-88a5-96164bfdd25f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IProbeMessage.Probe Method (COM)
Checks if the incoming message is in a recognizable format.  
  
## Syntax  
  
```cpp  
  
        HRESULT IProbeMessage::Probe(  
        IPipelineContext*  
        pContext,  
IBaseMessage*pInMsg,  
VARIANT_BOOL*pRet);  
```  
  
```vb  
  
        Function Probe(  
        pContext  
         As IPipelineContext,  
pInMsg As IBaseMessage) As Boolean  
```  
  
#### Parameters  
 *pContext*  
 [in] Reference to a **IPipelineContext** object/interface that contains the current pipeline context.  
  
 *pContext*  
 **IPipelineContext** object/interface that contains the current pipleine context.  
  
 *pInMsg*  
 [in] Reference to a **IBaseMessage** object/interface that contains the incoming message.  
  
 *pInMsg*  
 **IBaseMessage** object/interface that contains the incoming message.  
  
 *pRet*  
 [out,retval] Pointer to a Variant Boolean. **true** if the format was recognized; otherwise, **false**  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns **true** if the format was recognized; otherwise, **false**.  
  
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
 [IProbeMessage Interface (COM)](../core/iprobemessage-interface-com.md)   
 [IProbeMessage Members (COM)](../core/iprobemessage-members-com.md)