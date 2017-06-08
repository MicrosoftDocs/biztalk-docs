---
title: "IBaseMessageContext.AddPredicate Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1bd4386-86ab-4b58-af17-ad837a763c59
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.AddPredicate Method (COM)
Adds a message predicate to the message.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessageContext::AddPredicate(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANTVar);  
```  
  
```vb  
  
        Sub AddPredicate(  
        bstrName  
         As String,  
bstrNamespace As String,  
Var As Variant)  
```  
  
#### Parameters  
 *bstrName*  
 [in] String that contains the host property name.  
  
 *bstrName*  
 **String** that contains the host property name.  
  
 *bstrNamespace*  
 [in] String that contains the host property namespace.  
  
 *bstrNamespace*  
 **String** that contains the host property namespace.  
  
 *Var*  
 [in] Variant that contains the value to be matched against the host property value.  
  
 *Var*  
 **Variant** that contains the value to be matched against the host property value.  
  
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
 The MessageBox only supports the equals operation for message predicates.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessageContext Interface (COM)](../core/ibasemessagecontext-interface-com.md)   
 [IBaseMessageContext Members (COM)](../core/ibasemessagecontext-members-com.md)