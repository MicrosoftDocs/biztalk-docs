---
title: "IBaseMessage.GetPartByIndex Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d49630b-6d5c-481c-aff5-91385cac232c
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.GetPartByIndex Method (COM)
Retrieves a part and its name by supplying the part index.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessage::GetPartByIndex(  
        LONG  
        index,  
BSTR*pbstrPartName,  
IBaseMessagePart**ppPart);  
```  
  
```vb  
  
        Function GetPartByIndex(  
        index  
         As Long,  
pbstrPartName As String) As IBaseMessagePart  
```  
  
#### Parameters  
 *index*  
 [in] Integer that contains the index.  
  
 *index*  
 **Long** that contains the index.  
  
 *pbstrPartName*  
 [out] Pointer to a string used to return the part name.  
  
 *pbstrPartName*  
 **String** used to return the part name.  
  
 *ppPart*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns an [IBaseMessagePart](../core/ibasemessagepart-interface-com.md) containing the message part.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|E_INVALIDARG|A parameter that is not valid was detected.|  
  
## Remarks  
 This method is useful for enumerating all the parts within a message.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessage Interface (COM)](../core/ibasemessage-interface-com.md)   
 [IBaseMessage Members (COM)](../core/ibasemessage-members-com.md)