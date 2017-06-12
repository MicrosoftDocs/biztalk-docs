---
title: "ISSOMapper.GetMappingsForWindowsUser Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fde9d47f-7f64-4529-a687-3266fd57b8d6
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOMapper.GetMappingsForWindowsUser Method
The **GetMappingsForWindowsUser** method retrieves the mappings for a Microsoft Windows user.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetMappingsForWindowsUser(  
BSTR bstrWindowsDomainName,  
BSTR bstrWindowsUserName,  
BSTR bstrApplicationName,  
SAFEARRAY mappings  
);  
```  
  
```vb  
  
Function GetMappingsForWindowsUser(  
bstrWindowsDomainName As String,  
bstrWindowsUserName As String,  
bstrApplicationName As String  
)  
As Variant  
```  
  
#### Parameters  
 bstrWindowsDomainName  
 [in]  String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.  
  
 bstrWindowsDomainName  
 [in]  String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.  
  
 bstrWindowsUserName  
 [in]  String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.  
  
 bstrWindowsUserName  
 [in]  String that specifies the Microsoft Windows domain name. This parameter is optional, but if it is specified, the *windowsUserName* parameter must also be specified. If this parameter is not specified, the current user context is used.  
  
 bstrApplicationName  
 [in]  String that specifies the external application name. If this parameter is specified, only one mapping is returned if it exists. If this parameter is NULL, all mappings for the specified user are returned. This parameter is optional.  
  
 bstrApplicationName  
 [in]  String that specifies the external application name. If this parameter is specified, only one mapping is returned if it exists. If this parameter is NULL, all mappings for the specified user are returned. This parameter is optional.  
  
 mappings  
 [out]  Object array that contains the mappings as **ISSOMapping** objects.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Variant array that contains the mappings as **ISSOMapping** objects.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 An Application Administrator must specify the *bstrApplicationName* value.  
  
 Users described as Application User can only access their own mappings. They cannot access the mappings for another user.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapper Interface (COM)](../core/issomapper-interface-com.md)   
 [ISSOMapper Members](../core/issomapper-members.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)