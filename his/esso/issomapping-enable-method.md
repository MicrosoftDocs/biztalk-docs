---
title: "ISSOMapping.Enable Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68354946-9c9d-41a3-9f7c-24ff40e72538
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../esso/includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapping Interface (COM)](../esso/issomapping-interface-com.md)   
 [ISSOMapping Members](../esso/issomapping-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)