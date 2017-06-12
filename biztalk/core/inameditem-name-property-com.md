---
title: "INamedItem.Name Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52a11191-c5e5-4288-8f06-2ef2662fb9ff
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# INamedItem.Name Property (COM)
Gets the name of the item.  
  
## Syntax  
  
```cpp  
  
HRESULT INamedItem::get_Name(  
BSTR*  
Name  
);  
  
```  
  
```vb  
  
Property Name() As String  
  
```  
  
#### Parameters  
 *Name*  
 [out,retval] String used to return the name.  
  
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