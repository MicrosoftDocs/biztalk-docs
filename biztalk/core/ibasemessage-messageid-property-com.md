---
title: "IBaseMessage.MessageID Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6fd85b4-3ad7-4884-8a80-025cdbd3630c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.MessageID Property (COM)
Gets the unique message ID for the message and binds all the message parts together.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessage::get_MessageID(  
GUID*  
MessageID  
);  
  
```  
  
```vb  
  
Property MessageID() As GUID  
```  
  
#### Parameters  
 *MessageID*  
 [out,retval] Globally unique identifier (GUID) used to return the message ID.  
  
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
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)