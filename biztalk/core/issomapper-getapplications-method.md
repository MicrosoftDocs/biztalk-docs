---
title: "ISSOMapper.GetApplications Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69099b5a-7844-4945-9af6-6267c14ce8e7
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
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
 [ISSOMapper Interface (COM)](../core/issomapper-interface-com.md)   
 [Programming with Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)