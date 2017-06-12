---
title: "IBaseMessage.BodyPartName Property (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d4a3c71-8385-45f7-b214-c7108b95b67a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.BodyPartName Property (COM)
Gets the name of the body part, or main part, of the message.  
  
## Syntax  
  
```cpp  
  
HRESULT IBaseMessage::get_BodyPartName(  
BSTR*  
BodyPartName  
);  
  
```  
  
```vb  
  
Property BodyPartName() As String  
  
```  
  
#### Parameters  
 *BodyPartName*  
 [out,retval] String used to return the body part name.  
  
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
  
## Remarks  
 Each message must have at most one body part. A part can be the body part of one message and a non-body part of another message.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)