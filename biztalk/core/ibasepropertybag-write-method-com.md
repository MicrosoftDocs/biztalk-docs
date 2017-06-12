---
title: "IBasePropertyBag.Write Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7a1e8bf-a3dd-49a0-bad1-9bc05f383aab
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBasePropertyBag.Write Method (COM)
Adds or overwrites a property in the property bag.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBasePropertyBag::Write(  
        BSTR  
        bstrName,  
BSTRbstrNameSpace,  
VARIANTvar);  
```  
  
```vb  
  
        Sub Write(  
        bstrName  
         As String,  
bstrNameSpace As String,  
var As Variant)  
```  
  
#### Parameters  
 *bstrName*  
 [in] String that contains the name.  
  
 *bstrName*  
 **String** that contains the name.  
  
 *bstrNameSpace*  
 [in] String that contains the name space.  
  
 *bstrNameSpace*  
 **String** that contains the name space.  
  
 *var*  
 [in] Variant that contains the context property value.  
  
 *var*  
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
 If vtVar is equal to VT_NULL, the property is deleted.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBasePropertyBag Interface (COM)](../core/ibasepropertybag-interface-com.md)   
 [IBasePropertyBag Members (COM)](../core/ibasepropertybag-members-com.md)