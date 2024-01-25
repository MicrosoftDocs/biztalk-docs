---
description: "Learn more about: ISSOMapper.GetMappingsForExternalUser Method"
title: "ISSOMapper.GetMappingsForExternalUser Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOMapper.GetMappingsForExternalUser Method
The **GetMappingsForExternalUser** method retrieves the mappings for an external user.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetMappingsForExternalUser(  
BSTR bstrApplicationName,  
BSTR bstrExternalUserName,  
SAFEARRAY mappings  
);  
```  
  
```vb  
  
Function GetMappingsForExternalUser(  
bstrApplicationName As String,  
bstrExternalUserName As String)  
As Variant  
  
```  
  
#### Parameters  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `bstrExternalUserName`  
 [in]  String that specifies the external user name. This value can contain spaces. If a NULL value is specified for this parameter, all mappings are returned for the specified application.  
  
 `bstrExternalUserName`  
 [in]  String that specifies the external user name. This value can contain spaces. If a NULL value is specified for this parameter, all mappings are returned for the specified application.  
  
 `mappings`  
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
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapper Interface (COM)](../esso/issomapper-interface-com.md)   
 [ISSOMapper Members](../esso/issomapper-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
