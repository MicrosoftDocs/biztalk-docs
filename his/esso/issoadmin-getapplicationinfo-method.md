---
description: "Learn more about: ISSOAdmin.GetApplicationInfo Method"
title: "ISSOAdmin.GetApplicationInfo Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2358ba56-5af6-49dc-8229-c1a9899c9ac1
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOAdmin.GetApplicationInfo Method
The **GetApplicationInfo** method gets the application information from the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetApplicationInfo(  
BSTR bstrApplicationName,  
BSTR* pbstrDescription,  
BSTR* pbstrContactInfo,  
BSTR* pbstrUserGroupName,  
BSTR* pbstrAdminGroupName,  
LONG* plFlags,  
LONG* plNumFields  
);  
```  
  
```vb  
  
Function GetApplicationInfo(  
bstrApplicationName As String,  
pbstrDescription As String,  
pbstrContactInfo As String,  
pbstrUserGroupName As String,  
pbstrAdminGroupName As String,  
plFlags As Long  
)  
As Long  
```  
  
#### Parameters  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 pbstrDescription  
 [out]  Pointer to a string that receives the description for the application.  
  
 pbstrDescription  
 [out]  String that receives the description for the application.  
  
 pbstrContactInfo  
 [out]  Pointer to a string that receives the contact information for the application.  
  
 pbstrContactInfo  
 [out]  String that receives the contact information for the application.  
  
 pbstrUserGroupName  
 [out]  Pointer to a string that receives the application user group name.  
  
 pbstrUserGroupName  
 [out]  String that receives the application user group name.  
  
 pbstrAdminGroupName  
 [out]  Pointer to a string that receives the Application Administrator group name.  
  
 pbstrAdminGroupName  
 [out]  String that receives the Application Administrator group name.  
  
 plFlags  
 [out]  Pointer to a long integer that receives the flags currently set for the application.  
  
 plFlags  
 [out]  Long that receives the flags currently set for the application.  
  
 plNumFields  
 [out]  Pointer to a long integer that receives the number of fields associated with the application.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 This method returns a Long that receives the number of fields associated with the application.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an SSO Application Administrator.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)   
 [ISSOAdmin Interface (COM)](../esso/issoadmin-interface-com.md)   
 [ISSOAdmin Members](../esso/issoadmin-members.md)
