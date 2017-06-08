---
title: "IBaseMessagePart.Charset Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 205422d8-d396-4783-b849-a086946bf93e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.Charset Property (COM)
Accesses the character set property for the part.  
  
## Syntax  
  
```cpp  
  
            HRESULT IBaseMessagePart::get_Charset(  
            BSTR*  
            Charset  
            );   
HRESULT IBaseMessagePart::put_Charset(BSTRCharset);  
```  
  
```vb  
  
Property Charset() As String  
  
```  
  
#### Parameters  
 *Charset*  
 [in] When putting the property, a string that contains the character set. [out, retval] When getting the property, a string used to return the character set.  
  
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
 This property is also available in the [PartProperties](../core/ibasemessagepart-partproperties-property-com.md) property, the property bag for the part.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)