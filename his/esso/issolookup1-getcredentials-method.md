---
title: "ISSOLookup1.GetCredentials Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0670e766-9722-4c9a-9f12-ea14d885c6c6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOLookup1.GetCredentials Method
The **GetCredentials** method retrieves the user credentials for an application.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetCredentials(  
BSTR bstrApplicationName,  
LONG lFlags,  
BSTR* pbstrExternalUserName,  
SAFEARRAY credentials  
);  
```  
  
```vb  
  
Function GetCredentials(  
bstrApplicationName As String,  
lFlags As Long,  
pbstrExternalUserName As String  
)  
As String  
```  
  
#### Parameters  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `bstrApplicationName`  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 `lFlags`  
 [in]  Long integer that specifies the flags to set. Using the SSO_FLAG_REFRESH indicates that the credential cache should be bypassed.  
  
 `lFlags`  
 [in]  Long that specifies the flags to set. Using the SSO_FLAG_REFRESH indicates that the credential cache should be bypassed.  
  
 `pbstrExternalUserName`  
 [out]  Pointer to a string that receives the external user name.  
  
 `pbstrExternalUserName`  
 [out]  String that receives the external user name.  
  
 `credentials`  
 [out]  String array that receives the credentials.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 String array that receives the credentials.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 To access this method, you must be an Application User. You can only retrieve your own credential.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOLookup1 Interface (COM)](../esso/issolookup1-interface-com.md)   
 [ISSOLookup1 Members](../esso/issolookup1-members.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)