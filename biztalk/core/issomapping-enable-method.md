---
title: "ISSOMapping.Enable Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38d7a0b4-7d61-4234-9dfa-d8d13e0cbe41
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOMapping.Enable Method
The **Enable** method enables the mapping.  
  
## Syntax  
  
```cpp#  
  
HRESULT Enable(  
LONG lFlags  
);  
```  
  
```vb  
  
Sub Enable(  
lFlags As Long  
)  
```  
  
#### Parameters  
 `lFlags`  
 Not currently implemented.  
  
 `lFlags`  
 Not currently implemented.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapping Interface (COM)](../core/issomapping-interface-com.md)   
 [ISSOMapping Members](../core/issomapping-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)