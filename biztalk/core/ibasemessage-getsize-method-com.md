---
title: "IBaseMessage.GetSize Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed17043f-112c-40cc-951f-dbc663979822
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.GetSize Method (COM)
Gets the size of the message.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessage::GetSize(  
        ULARGE_INTEGER*  
        pVal,  
BOOL*pfImplemented);  
```  
  
```vb  
  
Function GetSize(  
pVal  
 As ULARGE_INTEGER  
) As Boolean  
  
```  
  
#### Parameters  
 *pVal*  
 [out] Pointer to a **ULARGE_INTEGER** used to return the size of the message.  
  
 *pVal*  
 ULARGE_INTEGER used to return the size of the message.  
  
 *pfImplemented*  
 [out, retval] Pointer to a Boolean used to return the results of the counting operation. **true** if the [IBaseMessage](../core/ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns **true** if the [IBaseMessage](../core/ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.  
  
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
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)