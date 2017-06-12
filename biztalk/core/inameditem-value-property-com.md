---
title: "INamedItem.Value Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78e8c20f-8caa-43ff-a882-f6b03edcc2a3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# INamedItem.Value Property (COM)
Gets the value of the item.  
  
## Syntax  
  
```cpp  
  
HRESULT INamedItem::get_Value(  
IUnknown**  
Value  
);  
  
```  
  
```vb  
  
Property Value() As IUnknown  
  
```  
  
#### Parameters  
 *Value*  
 [out,retval] **IUnknown** interface used to return the value.  
  
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
 [INamedItem Interface (COM)](../core/inameditem-interface-com.md)   
 [INamedItem Members (COM)](../core/inameditem-members-com.md)