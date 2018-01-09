---
title: "ISSOMapper2.GetApplications2 Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd2457b8-8461-4a6f-bedd-f5def73d3cd3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ISSOMapper2.GetApplications2 Method
The GetApplications2 method retrieves the available applications for a Microsoft Windows user.  
  
## Syntax  
  
```vb  
  
Sub GetApplications2(  
applications As String,   
descriptions As String,   
contactInfo As String,   
userAccounts As String,   
adminAccounts As String,   
flags As Long  
);  
```  
  
```csharp  
  
HRESULT GetApplications2(  
SAFEARRAY applications,   
SAFEARRAY descriptions,   
SAFEARRAY contactInfo,   
SAFEARRAY userAccounts,   
SAFEARRAY adminAccounts,   
SAFEARRAY flags  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`applications`|String array that returns the application name.|  
|`descriptions`|String array that returns a description of the application.|  
|`contactInfo`|String array that returns the contact information for the application.|  
|`userAccounts`|String array that returns all user accounts for the application. GetApplications2 returns a null in this parameter when called by an application user.|  
|`adminAccounts`|String array that returns all administration accounts for the application. GetApplications2 returns a null in this parameter when called by an application user.|  
|`flags`|Integer array that returns the flags for the application.|  
  
## Property Value/Return Value  
 [C++] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 [Visual Basic] Not Applicable.  
  
## Exceptions  
 [C++] This method returns an HRESULT containing one of the values in the following table.  
  
 [Visual Basic] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDREG|An invalid parameter was detected.|