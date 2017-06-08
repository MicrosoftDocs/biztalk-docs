---
title: "IBaseMessage.BodyPart Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e683722a-b707-4d41-8a8d-1baf742cfe1a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.BodyPart Property (COM)
Gets the body part, or main part, of the message.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessage::get_BodyPart(  
IBaseMessagePart**  
BodyPart  
);  
  
```  
  
```vb  
  
Property BodyPart() As IBaseMessagePart  
  
```  
  
#### Parameters  
 *BodyPart*  
 [out,retval] **IBaseMessagePart** used to return the body part.  
  
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
  
## Remarks  
 Each message must have at most one body part. A part can be the body part of one message and a non-body part of another message.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)