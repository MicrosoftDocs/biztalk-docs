---
title: "ISSOAdmin.DeleteApplication Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6accf27-285f-4059-8df4-cbed39e71f01
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOAdmin.DeleteApplication Method
The **DeleteApplication** method deletes an application from the Enterprise Single Sign-On (SSO) server database.  
  
## Syntax  
  
```cpp#  
  
HRESULT DeleteApplication(  
BSTR bstrApplicationName  
);  
```  
  
```vb  
  
Sub DeleteApplication(  
bstrApplicationName As String  
)  
```  
  
#### Parameters  
 bstrApplicationName  
 [in] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrApplicationName  
 [in] String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|S_FALSE|The application was not found.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 All fields, mappings, and external credentials associated with this application are deleted.  
  
 To access this method, you must be an SSO Administrator or an SSO Affiliate Administrator.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)   
 [ISSOAdmin Interface (COM)](../core/issoadmin-interface-com.md)   
 [ISSOAdmin Members](../core/issoadmin-members.md)