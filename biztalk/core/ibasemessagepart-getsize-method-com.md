---
title: "IBaseMessagePart.GetSize Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ca648ba0-707a-4e1d-860b-2882b30c004f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessagePart.GetSize Method (COM)
Retrieves the size of the part.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessagePart::GetSize(  
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
 [out] Pointer to a **ULARGE_INTEGER** used to return the size of the object.  
  
 *pVal*  
 ULARGE_INTEGER used to return the size of the object.  
  
 *pfImplemented*  
 [out, retval] Pointer to a Boolean used to return the information if the message size can be determined. **true** if the [IBaseMessage](../core/ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 **true** if the [IBaseMessage](../core/ibasemessage-interface-com.md) object can determine the size; otherwise, **false**.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Remarks  
 If the message has already been persisted and the data is unchangeable, then this value is a stored value. If the message is new, then the value is calculated at the time of the call. For new messages, you can get different values depending on when in the pipeline or schedule you call into the message because the data can change.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessagePart Interface (COM)](../core/ibasemessagepart-interface-com.md)   
 [IBaseMessagePart Members (COM)](../core/ibasemessagepart-members-com.md)