---
title: "IBaseMessageContext.Read Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17da744e-c779-4765-b071-217eb08e782f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.Read Method (COM)
Gets the property value from the message context by the name-namespace pair.  
  
## Syntax  
  
```cpp  
  
         HRESULT IBaseMessageContext::Read(   
BSTR bstrName,   BSTR bstrNamespace,VARIANT *pVar);  
```  
  
```vb  
  
      Function Read( _   
bstrName As String, _bstrNamespace As String _) As Variant  
```  
  
#### Parameters  
 *bstrName*  
 [in] String that contains the property name.  
  
 *bstrName*  
 **String** that contains the property name.  
  
 *bstrNamespace*  
 [in] String that contains the property namespace.  
  
 *bstrNamespace*  
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