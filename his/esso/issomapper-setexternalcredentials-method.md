---
title: "ISSOMapper.SetExternalCredentials Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8066d28-285a-40ce-8cf5-e1be6b113ec1
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# ISSOMapper.SetExternalCredentials Method
The **SetExternalCredentials** method stores a set of external credentials in the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```cpp#  
  
HRESULT SetExternalCredentials(  
BSTR bstrApplicationName,  
BSTR bstrExternalUserName,  
SAFEARRAY externalCredentials  
);  
```  
  
```  
  
[Visual Basic]  
Sub SetExternalCredentials(  
bstrApplicationName As String,  
bstrExternalUserName As String,  
externalCredentials As String  
)  
```  
  
#### Parameters  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `bstrExternalUserName`  
 [in]  String that specifies the external user name.  
  
 `bstrExternalUserName`  
 [in]  String that specifies the external user name.  
  
 `externalCredentials`  
 [in]  String array that specifies the external credentials to be stored.  
  
 `externalCredentials`  
 [in]  String array that specifies the external credentials to be stored.  
  
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
  
## Remarks  
 Users described as Application User can only set their own credentials. Also, the number of external credentials provided must match the number of fields expected by the external application.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../esso/includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapper Interface (COM)](../esso/issomapper-interface-com.md)   
 [ISSOMapper Members](../esso/issomapper-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)