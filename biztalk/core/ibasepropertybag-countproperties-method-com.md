---
title: "IBasePropertyBag.CountProperties Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3701a2a2-fdc5-4e50-bb25-7c6c6fdb5c9c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBasePropertyBag.CountProperties Method (COM)
Gets the number of properties in the property bag.  
  
## Syntax  
  
```cpp  
  
HRESULT IBasePropertyBag::CountProperties(  
ULONG*  
cCount  
);  
  
```  
  
```vb  
  
Sub CountProperties(  
cCount  
 As ULONG  
)  
  
```  
  
#### Parameters  
 *cCount*  
 [out] Pointer to a **ULONG** used to return the number of properties in the property bag.  
  
 *cCount*  
 ULONG used to return the number of properties in the property bag.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 None.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBasePropertyBag Interface (COM)](../core/ibasepropertybag-interface-com.md)   
 [IBasePropertyBag Members (COM)](../core/ibasepropertybag-members-com.md)