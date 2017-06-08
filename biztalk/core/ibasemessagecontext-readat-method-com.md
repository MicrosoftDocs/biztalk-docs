---
title: "IBaseMessageContext.ReadAt Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4aaa5be-7d8e-4e84-8368-229b22410d45
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.ReadAt Method (COM)
Gets the property from the message context by index.  
  
## Syntax  
  
```cpp  
  
    HRESULT IBaseMessageContext::ReadAt(   
Long index,BSTR* pbstrName,BSTR* pbstrNamespace,VARIANT *pVar);  
```  
  
```vb  
  
      Function ReadAt( _   
index As Long, _pbstrName As String, _pbstrNamespace As String _) As Variant  
```  
  
#### Parameters  
 *index*  
 [in] The position of the property to read.  
  
 *index*  
 The position of the property to read.  
  
 *pbstrName*  
 [in] String that contains the property name.  
  
 *pbstrName*  
 **String** that contains the property name.  
  
 *pbstrNamespace*  
 [in] String that contains the property namespace.  
  
 *pbstrNamespace*  
 **String** that contains the property namespace.  
  
 *pVar*  
 [out,retval] Pointer to a Variant used to return the message context property value.  
  
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
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessageContext Interface (COM)](../core/ibasemessagecontext-interface-com.md)   
 [IBaseMessageContext Members (COM)](../core/ibasemessagecontext-members-com.md)