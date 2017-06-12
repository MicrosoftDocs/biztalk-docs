---
title: "IBaseMessagePart.Data Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 463b8e0c-2fe5-4ac0-acc6-893f6ec0be98
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.Data Property (COM)
Accesses the part data.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessagePart::get_Data(  
  IStream** Data  
);  
HRESULT IBaseMessagePart::put_Data(IStream*Data);  
```  
  
```vb  
  
Property Data() As IStream  
  
```  
  
#### Parameters  
 *Data*  
 [in] When putting the property, an **IStream** that contains the part data. [out,retval] When getting the property, an **IStream** used to return the part data.  
  
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
 For messages delivered by the Messaging Engine, the part data for the attachment parts are loaded only on demand.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)