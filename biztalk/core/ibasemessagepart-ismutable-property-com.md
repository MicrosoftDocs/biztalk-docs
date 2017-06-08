---
title: "IBaseMessagePart.IsMutable Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5b8b885-6e3a-4c31-9351-07cac7c4c4b7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.IsMutable Property (COM)
Gets a value that indicates whether the message context can be changed by components during processing.  
  
## Syntax  
  
```cpp  
  
          HRESULT IBaseMessagePart::get_IsMutable(   
BOOLIsMutable);  
```  
  
```vb  
  
Public ReadOnly Property IsMutable As Boolean  _  
  
```  
  
#### Parameters  
 *IsMutable*  
 [out,retval] **true** if the value can be changed; otherwise, **false**.  
  
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