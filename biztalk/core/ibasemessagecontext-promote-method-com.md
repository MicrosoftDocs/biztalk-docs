---
title: "IBaseMessageContext.Promote Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd845a40-1de1-48b8-9d3e-e8ce7db91428
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.Promote Method (COM)
Promotes the property into the message context.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBaseMessageContext::Promote(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANTVar);  
```  
  
```vb  
  
        Sub Promote(  
        bstrName  
         As String,  
bstrNamespace As String,  
Var As Variant)  
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
  
 *Var*  
 [in] Variant that contains the context property value.  
  
 *Var*  
 **Variant** that contains the context property value.  
  
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
 When the message is published, the promoted properties are extracted from the context and written to the database as clear values. All the promoted properties for a message are used for subscription evaluation.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessageContext Interface (COM)](../core/ibasemessagecontext-interface-com.md)   
 [IBaseMessageContext Members (COM)](../core/ibasemessagecontext-members-com.md)