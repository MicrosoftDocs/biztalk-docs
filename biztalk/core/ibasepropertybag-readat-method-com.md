---
title: "IBasePropertyBag.ReadAt Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 631c5fb0-1dd7-4e17-8b4e-1186c521c309
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBasePropertyBag.ReadAt Method (COM)
Reads the property at the specified index value in the property bag.  
  
## Syntax  
  
```cpp  
  
        HRESULT IBasePropertyBag::ReadAt(  
        LONG  
        index,  
BSTR*pbstrName,  
BSTR*pbstrNamespace,  
VARIANT*pVar);  
```  
  
```vb  
  
        Function ReadAt(  
        index  
         As Long,  
pbstrName As String,  
pbstrNamespace As String) As Variant  
```  
  
#### Parameters  
 *index*  
 [in] Integer that contains the index.  
  
 *index*  
 **Long** that contains the index.  
  
 *pbstrName*  
 [out] Pointer to a string used to return the property name.  
  
 *pbstrName*  
 **String** used to return the property name.  
  
 *pbstrNamespace*  
 [out] Pointer to a string used to return the property namespace.  
  
 *pbstrNamespace*  
 **String** used to return the property namespace.  
  
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
  
## Remarks  
 This method is useful for enumerating properties. Properties are indexed in the order in which they were added to the property bag.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBasePropertyBag Interface (COM)](../core/ibasepropertybag-interface-com.md)   
 [IBasePropertyBag Members (COM)](../core/ibasepropertybag-members-com.md)