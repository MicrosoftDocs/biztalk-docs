---
title: "IBaseMessage.AddPart Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a29f9147-d283-4928-9a75-297f854346ed
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.AddPart Method (COM)
Adds a part to the message.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessage::AddPart(  
        BSTR  
        bstrPartName,  
IBaseMessagePart*pPart,  
BOOLbIsBody);  
```  
  
```vb  
  
        Sub AddPart(  
        bstrPartName  
         As String,  
pPart As IBaseMessagePart,  
bIsBody As Boolean)  
```  
  
#### Parameters  
 *bstrPartName*  
 [in] String that contains the part name.  
  
 *bstrPartName*  
 **String** that contains the part name.  
  
 *pPart*  
 [in] Reference to a **IBaseMessagePart** object/interface that contains the part.  
  
 *pPart*  
 **IBaseMessagePart** object/interface that contains the part.  
  
 *bIsBody*  
 [in] Boolean that identifies whether the part is a body part. **true** indicates the part is a body part; otherwise, **false**.  
  
 *bIsBody*  
 **Boolean** that identifies whether the part is a body part. **true** indicates the part is a body part; otherwise, **false**.  
  
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
  
## Remarks  
 The part name must be unique within the message.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)