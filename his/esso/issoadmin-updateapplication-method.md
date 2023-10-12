---
description: "Learn more about: ISSOAdmin.UpdateApplication Method"
title: "ISSOAdmin.UpdateApplication Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOAdmin.UpdateApplication Method
The **UpdateApplication** method updates the application information in the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```cpp#  
  
HRESULT UpdateApplication(  
BSTR bstrApplicationName,  
BSTR bstrDescription,  
BSTR bstrContactInfo,  
BSTR bstrUserGroupName,  
BSTR bstrAdminGroupName,  
LONG lFlags,  
LONG lFlagMask  
);  
```  
  
```vb  
  
Function UpdateApplication(  
bstrApplicationName As String,  
bstrDescription As String,  
bstrContactInfo As String,  
bstrUserGroupName As String,  
bstrAdminGroupName As String,  
lFlags As Long  
)  
```  
  
#### Parameters  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrDescription  
 [in]  String that specifies the description of the application.  
  
 bstrDescription  
 [in]  String that specifies the description of the application.  
  
 bstrContactInfo  
 [in]  String that specifies the contact information for this application.  
  
 bstrContactInfo  
 [in]  String that specifies the contact information for this application.  
  
 bstrUserGroupName  
 [in]  String that specifies the Application Users group name. This must be a valid global group.  
  
 bstrUserGroupName  
 [in]  String that specifies the Application Users group name. This must be a valid global group.  
  
 bstrAdminGroupName  
 [in]  String that specifies the Application Administrator group name. This must be a valid global group. If running as an Application Administrator, this parameter will be ignored.  
  
 bstrAdminGroupName  
 [in]  String that specifies the Application Administrator group name. This must be a valid global group. If running as an Application Administrator, this parameter will be ignored.  
  
 lFlags  
 [in]  Integer that specifies whether the application is enabled. To enable the application, set the SSO_FLAG_ENABLED flag.  
  
 lFlags  
 [in]  Integer that specifies whether the application is enabled. To enable the application, set the SSO_FLAG_ENABLED flag.  
  
 lFlagMask  
 [in]  To change the flag value, set this mask to the flag that you need to change. For example, to enable or disable Enterprise SSO, set this flag to SSO_FLAG_ENABLED. The *flagMask* parameter indicates which flag you want to change, while the *flags* parameter indicates the new value of that flag.  
  
 lFlagMask  
 [in]  To change the flag value, set this mask to the flag that you need to change. For example, to enable or disable Enterprise SSO, set this flag to SSO_FLAG_ENABLED. The *flagMask* parameter indicates which flag you want to change, while the *flags* parameter indicates the new value of that flag.  
  
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
 To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)   
 [ISSOAdmin Interface (COM)](../esso/issoadmin-interface-com.md)   
 [ISSOAdmin Members](../esso/issoadmin-members.md)
