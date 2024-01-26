---
description: "Learn more about: ISSOAdmin.CreateApplication Method"
title: "ISSOAdmin.CreateApplication Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOAdmin.CreateApplication Method
The **CreateApplication** method creates an application in the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```cpp#  
  
HRESULT CreateApplication(  
BSTR bstrApplicationName,  
BSTR bstrDescription,  
BSTR bstrContactInfo,  
BSTR bstrUserGroupName,  
BSTR bstrAdminGroupName,  
LONG lFlags,  
LONG lNumFields  
);  
```  
  
```  
  
[Visual Basic]  
Sub CreateApplication(  
bstrApplicationName As String,  
bstrDescription As String,  
bstrContactInfo As String,  
bstrUserGroupName As String,  
bstrAdminGroupName As String,  
lFlags As Long,  
lNumFields As Long  
)  
```  
  
#### Parameters  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrDescription  
 [in]  String that specifies the description for the application. This parameter can be NULL, an empty string, or contain spaces.  
  
 bstrDescription  
 [in]  String that specifies the description for the application. This parameter can be NULL, an empty string, or contain spaces.  
  
 bstrContactInfo  
 [in]  String that specifies the contact information for this application. This parameter can be NULL, an empty string, or contain spaces.  
  
 bstrContactInfo  
 [in]  String that specifies the contact information for this application. This parameter can be NULL, an empty string, or contain spaces.  
  
 bstrUserGroupName  
 [in]  String that specifies the application users group name. This parameter must contain a valid global group.  
  
 bstrUserGroupName  
 [in]  String that specifies the application users group name. This parameter must contain a valid global group.  
  
 bstrAdminGroupName  
 [in]  String that specifies the Application Administrator group name. This parameter must contain a valid global group.  
  
 bstrAdminGroupName  
 [in]  String that specifies the Application Administrator group name. This parameter must contain a valid global group.  
  
 lFlags  
 [in]  Long integer that specifies whether the application is a group application. If a group application is required, specify SSO_FLAG_APP_USES_GROUP_MAPPING.  
  
 lFlags  
 [in]  Long integer that specifies whether the application is a group application. If a group application is required, specify SSO_FLAG_APP_USES_GROUP_MAPPING.  
  
 lNumFields  
 [in]  Long integer that specifies the number of fields that will be added for this application. The minimum value is 1 (one external user ID). An application can have no credential fields.  
  
 lNumFields  
 [in]  Long integer that specifies the number of fields that will be added for this application. The minimum value is 1 (one external user ID). An application can have no credential fields.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 An application is always created as disabled.  
  
 After the field information is added by using the **CreateFieldInfo** method, then the application can be enabled by using the **UpdateApplication** method. The number of fields added by **CreateFieldInfo** must match the number of fields specified by the *numFields* parameter. The *numFields* value cannot be changed after the application is created.  
  
 To access this method, you must be an SSO Administrator or an SSO Affiliate Administrator.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)   
 [ISSOAdmin Interface (COM)](../esso/issoadmin-interface-com.md)   
 [ISSOAdmin Members](../esso/issoadmin-members.md)
