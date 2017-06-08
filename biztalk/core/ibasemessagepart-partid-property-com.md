---
title: "IBaseMessagePart.PartID Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ee35a62-d72b-42d0-b9f2-4f33ec3acec0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.PartID Property (COM)
Gets the unique ID for the part.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessagePart::get_PartID(  
GUID*  
PartID  
);  
  
```  
  
```vb  
  
Property PartID() As GUID  
```  
  
#### Parameters  
 *PartID*  
 [out,retval] Globally unique identifier (GUID) used to return the part ID.  
  
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
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)