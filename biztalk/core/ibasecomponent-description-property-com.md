---
title: "IBaseComponent.Description Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4387905-2f54-48cc-a0d0-681f0f85ca4c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseComponent.Description Property (COM)
Gets the component description.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseComponent::get_Description(  
BSTR*  
Description  
);  
  
```  
  
```vb  
  
Property Description() As String  
  
```  
  
#### Parameters  
 *Description*  
 [out,retval] String used to return the description of the component.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
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
 [IBaseComponent Interface (COM)](../core/ibasecomponent-interface-com.md)   
 [IBaseComponent Members (COM)](../core/ibasecomponent-members-com.md)