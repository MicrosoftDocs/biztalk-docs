---
title: "ISSOAdmin.PurgeCacheForApplication Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28e49ab8-3a67-452c-8263-58903e7709e9
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOAdmin.PurgeCacheForApplication Method
The **PurgeCacheForApplication** method purges the cached credentials for an application on all Enterprise Single Sign-On (SSO) servers.  
  
## Syntax  
  
```cpp#  
  
HRESULT PurgeCacheForApplication(  
BSTR bstrApplicationName  
);  
```  
  
```vb  
  
Sub PurgeCacheForApplication(  
bstrApplicationName As String  
)  
```  
  
#### Parameters  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
 bstrApplicationName  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are not case-sensitive, but case will be preserved. For example, ABC, abc, and AbC are considered to be the same application.  
  
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
 There may be a short time delay while this operation is applied to all SSO servers.  
  
 To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)   
 [ISSOAdmin Interface (COM)](../core/issoadmin-interface-com.md)   
 [ISSOAdmin Members](../core/issoadmin-members.md)