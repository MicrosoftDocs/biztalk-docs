---
title: "IBasePropertyBag.Read Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f16bd8a-e7ba-4e47-afa0-b01ca47f2bd6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBasePropertyBag.Read Method (COM)
Reads the value and type of the given property in the property bag.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBasePropertyBag::Read(  
        BSTR  
        bstrName,  
BSTRbstrNamespace,  
VARIANT*pVar);  
```  
  
```vb  
  
        Function Read(  
        bstrName  
         As String,  
bstrNamespace As String) As Variant  
```  
  
#### Parameters  
 *bstrName*  
 [in] String that contains the name.  
  
 *bstrName*  
 **String** that contains the name.  
  
 *bstrNamespace*  
 [in] String that contains the namespace.  
  
 *bstrNamespace*  
 **String** that contains the namespace.  
  
 *pVar*  
 [out,retval] Pointer to a Variant used to return the message context property value.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 If this method completes successfully, it returns the message context property value.  
  
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
 [IBasePropertyBag Interface (COM)](../core/ibasepropertybag-interface-com.md)   
 [IBasePropertyBag Members (COM)](../core/ibasepropertybag-members-com.md)