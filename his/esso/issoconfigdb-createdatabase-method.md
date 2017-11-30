---
title: "ISSOConfigDB.CreateDatabase Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ada766a-e127-44b3-8de2-7e2689d4fc19
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOConfigDB.CreateDatabase Method
The CreateDatabase method creates a SQL database for SSO.  
  
## Syntax  
  
```vb  
  
Sub CreateDatabase(  
sqlServer As String,   
sqlDatabase As String,   
configureOnly As Boolean,   
secretServer As String,   
ssoAdminAccount As String,   
ssoAffilateAdminAccount As String  
);  
```  
  
```cpp#  
  
HRESULT CreateDatabase(  
BSTR sqlServer,   
BSTR sqlDatabase,   
bool configureOnly,   
BSTR secretServer,   
BSTR ssoAdminAccount,   
BSTR ssoAffilateAdminAccount  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`sqlServer`|String containing the name of the SQL server for the database.|  
|`sqlDatabase`|String containing the name of the SQL database.|  
|`configureOnly`|True to configure an already-existing database; otherwise, false.|  
|`secretServer`|String containing the name of the secret server.|  
|`ssoAdminAccount`|String containing the name of the SSO administration account for the server.|  
|`ssoAffilateAdminAccount`|String containing the name of the SSO affiliate administration account.|  
  
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