---
title: "IComponentUI.Icon Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ad8b610-4b75-451d-9452-c5fe69fdc1b1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IComponentUI.Icon Property (COM)
Provides the icon that is associated with this component.  
  
## Syntax  
  
```cpp  
  
HRESULT IComponentUI::get_Icon(  
IPicture**  
Icon  
);  
  
```  
  
```vb  
  
Property Icon() As IPicture  
  
```  
  
#### Parameters  
 *Icon*  
 [out,retval] **IPicture** used to return the icon.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IComponentUI Interface (COM)](../core/icomponentui-interface-com.md)