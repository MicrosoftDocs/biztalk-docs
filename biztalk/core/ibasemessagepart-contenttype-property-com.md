---
title: "IBaseMessagePart.ContentType Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e02744b5-713e-47bb-9b6f-ac074527a338
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.ContentType Property (COM)
Accesses the content type property for the part.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBaseMessagePart::get_ContentType(  
            BSTR*  
            ContentType  
            );   
HRESULT IBaseMessagePart::put_ContentType(BSTRContentType);  
```  
  
```vb  
  
Property ContentType() As String  
  
```  
  
#### Parameters  
 *ContentType*  
 [in] When putting the property, a string that contains the content type. [out, retval] When getting the property, a string used to return the content type.  
  
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
 This property is also available on the [PartProperties](../core/ibasemessagepart-partproperties-property-com.md) property, the property bag for the part.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)