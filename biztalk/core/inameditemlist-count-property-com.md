---
title: "INamedItemList.Count Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f23a437-d215-438c-9d89-8d8caeea35f5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# INamedItemList.Count Property (COM)
Gets the number of items in the list.  
  
## Syntax  
  
```cpp  
  
HRESULT INamedItemList::get_Count(  
LONG*  
Count  
);  
  
```  
  
```vb  
  
Property Count() As Long  
  
```  
  
#### Parameters  
 *Count*  
 [out,retval] Integer used to return the number of items in the list.  
  
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
 [INamedItemList Interface (COM)](../core/inameditemlist-interface-com.md)   
 [INamedItemList Members (COM)](../core/inameditemlist-members-com.md)