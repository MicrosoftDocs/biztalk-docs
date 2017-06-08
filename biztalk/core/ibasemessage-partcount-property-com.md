---
title: "IBaseMessage.PartCount Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f643699-4ff7-46ab-8c15-2bdb2421a235
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.PartCount Property (COM)
Gets the total number of parts in the message.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessage::get_PartCount(  
LONG*  
PartCount  
);  
  
```  
  
```vb  
  
Property PartCount() As Long  
  
```  
  
#### Parameters  
 *PartCount*  
 [out, retval] Integer used to return the number of parts in the message.  
  
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
 The **PartCount** property is incremented when a new part is added to the message.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)