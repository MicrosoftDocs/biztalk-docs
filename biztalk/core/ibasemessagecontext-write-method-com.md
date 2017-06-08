---
title: "IBaseMessageContext.Write Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc0e9c2f-43e8-470e-a285-86c4e7000f9e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBaseMessageContext.Write Method (COM)
Writes a property into the message context.  
  
## Syntax  
  
```cpp  
  
         HRESULT IBaseMessageContext::Write(   
BSTR bstrName,   BSTR bstrNamespace,   Variant var);  
```  
  
```vb  
  
      Sub Write( _   
bstrName As String, _bstrNamespace As String, _var As Variant _)  
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
  
 *var*  
 [in] Variant that contains the context property value.  
  
 *vare*  
 **Variant** that contains context property value.  
  
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
 The written property is not being promoted.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBaseMessageContext Interface (COM)](../core/ibasemessagecontext-interface-com.md)   
 [IBaseMessageContext Members (COM)](../core/ibasemessagecontext-members-com.md)