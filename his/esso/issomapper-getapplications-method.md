---
description: "Learn more about: ISSOMapper.GetApplications Method"
title: "ISSOMapper.GetApplications Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e36ea4d9-be48-4b6f-9c83-a6554540b87a
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# ISSOMapper.GetApplications Method
The **GetApplications** method retrieves the available applications for a Microsoft Windows user.  
  
## Syntax  
  
```cpp#  
  
HRESULT GetApplications(  
SAFEARRAY applications,  
SAFEARRAY descriptions,  
SAFEARRAY contactInfo  
)  
```  
  
```vb  
  
Sub GetApplications(  
applications As String,  
descriptions As String,   
contactInfo As String  
)  
```  
  
#### Parameters  
 `applications`  
 [out]  String array that returns the application name.  
  
 `applications`  
 [out]  String array that returns the application name.  
  
 `descriptions`  
 [out]  String array that returns a description for the application.  
  
 `descriptions`  
 [out]  String array that returns a description for the application.  
  
 `contactInfo`  
 [out]  String array that returns the contact information for the application.  
  
 `contactInfo`  
 [out]  String array that returns the contact information for the application.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 Not applicable.  
  
## Error Values  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the **Number** property of the global **Err** object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [ISSOMapper Interface (COM)](../esso/issomapper-interface-com.md)   
 [Programming with Enterprise Single Sign-On](../esso/programming-with-enterprise-single-sign-on.md)
