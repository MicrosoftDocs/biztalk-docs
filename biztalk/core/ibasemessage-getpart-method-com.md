---
title: "IBaseMessage.GetPart Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4797896e-dd93-482d-a786-959240fd9522
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessage.GetPart Method (COM)
Accesses the message parts.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessage::GetPart(  
        BSTR  
        bstrPartName,  
IBaseMessagePart**ppPart);  
```  
  
```vb  
  
Function GetPart(  
bstrPartName  
 As String  
) As IBaseMessagePart  
  
```  
  
#### Parameters  
 *bstrPartName*  
 [in] String that contains the part name.  
  
 *bstrPartName*  
 **String** that contains the part name.  
  
 *ppPart*  
 [out,retval] Pointer to hold the reference to the returned **IBaseMessagePart** object/interface, which will contain the part.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns a [IBaseMessagePart](../core/ibasemessagepart-interface-com.md) containing the part.  
  
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