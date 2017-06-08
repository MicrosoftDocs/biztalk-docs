---
title: "IBaseMessageContext.GetPropertyType Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49c3cb8b-0ab3-478f-9422-fcc2d09b74f3
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.GetPropertyType Method (COM)
Gets the type of the property.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessageContext::GetPropertyType(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
PropertyType*ppRet);  
```  
  
```vb  
  
        Function GetPropertyType(  
        bstrName  
         As String,  
bstrNamespace As String) As PropertyType  
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
  
 *ppRet*  
 [out,retval] Pointer to a **PropertyType**.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 **true** if the property has been marked for promotion; otherwise, **false**.  
  
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