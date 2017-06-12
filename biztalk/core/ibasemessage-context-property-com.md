---
title: "IBaseMessage.Context Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7aff1ff-04bc-440e-8dcd-925d25f3d4b4
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.Context Property (COM)
Represents the message context.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBaseMessage::get_Context( // Get method  
    IBaseMessageContext**Context);   
HRESULT IBaseMessage::put_Context( // Put method:  
    IBaseMessageContext*Context);  
```  
  
```vb  
  
Property Context() As IBaseMessageContext  
  
```  
  
#### Parameters  
 *Context*  
 [in] When putting the property, an **IBaseMessageContext** that contains the message context. [out, retval] When getting the property, an **IBaseMessageContext** used to return the message context.  
  
 None.  
  
## Return Value  
 These methods return an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
## Error Values  
 These methods return an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The property was successfully obtained or written.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Remarks  
 The component can add properties to the context; these properties are persisted in the database if the message is submitted to the BizTalk Server Messaging Engine by using the `[SubmitMessage` method of the `IBTTransportBatch` interface.  
  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)