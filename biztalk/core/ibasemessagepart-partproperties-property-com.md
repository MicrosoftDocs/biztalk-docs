---
title: "IBaseMessagePart.PartProperties Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fe67-53ed-447e-85c9-af022809cb73
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.PartProperties Property (COM)
Contains one or more properties that describe the part data or contain custom information about the part.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessagePart::get_PartProperties(  
IBasePropertyBag**  
PartProperties  
);  
HRESULT IBaseMessagePart::put_PartProperties(  
IBasePropertyBag*  
PartProperties  
);  
  
```  
  
```vb  
  
Property PartProperties() As IBasePropertyBag  
  
```  
  
#### Parameters  
 *PartProperties*  
 [in] When putting the property, an **IBasePropertyBag** that contains the part properties. [out, retval] When getting the property, an **IBasePropertyBag** used to return the part properties.  
  
 None.  
  
## Return Value  
 These methods return an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 Not applicable.  
  
## Error Values  
 These methods return an HRESULT containing one of the values in the following table.  
  
 This property indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The property was successfully obtained or written.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Remarks  
 Some of the properties contained in this property bag are also available on the part itself.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)