---
title: "ISSOMapping.WindowsDomainName Property | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f79fec5-c57a-48eb-9722-ac9988a00059
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOMapping.WindowsDomainName Property
The **WindowsDomainName** property specifies the Microsoft Windows domain name.  
  
## Syntax  
  
```cpp  
  
HRESULT ISSOMapping::get_WindowsDomainName(BSTR* WindowsDomainName);  
HRESULT ISSOMapping::put_WindowsDomainName(BSTR WindowsDomainName);  
  
```  
  
```vb  
  
Property WindowsDomainName() As String  
  
```  
  
#### Parameters  
 `WindowsDomainName`  
 [in] When putting the property, a string that contains the Windows domain name. Maximum length is 15 characters.  
  
 [out, retval] When getting the property, a string used to return the Windows domain name.  
  
 None.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapping Interface (COM)](../core/issomapping-interface-com.md)   
 [ISSOMapping Members](../core/issomapping-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)