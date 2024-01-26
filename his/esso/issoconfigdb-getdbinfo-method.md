---
description: "Learn more about: ISSOConfigDB.GetDBInfo Method"
title: "ISSOConfigDB.GetDBInfo Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOConfigDB.GetDBInfo Method
The GetDBInfo method retrieves information about the specified database.  
  
## Syntax  
  
```vb  
  
Sub GetDBInfo(  
sqlServer As String,   
sqlDatabase As String,   
exists As Boolean,   
isConfigured As Boolean,   
needsUpgrade As Boolean,   
secretServer As String,   
ssoAdminAccount As String,   
ssoAffilateAdminAccount As String  
);  
```  
  
```cpp#  
  
HRESULT GetDBInfo(  
string sqlServer,   
string sqlDatabase,   
out bool exists,   
out bool isConfigured,   
out bool needsUpgrade,   
out string secretServer,   
out string ssoAdminAccount,   
out string ssoAffilateAdminAccount  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`sqlServer`|String containing the name of the SQL server.|  
|`sqlDatabase`|String containing the name of the specified database.|  
|`exists`|Returns true if the database exists; otherwise, false.|  
|`isConfigured`|Returns true if the database is configured; otherwise, false.|  
|`needsUpgrade`|Returns true if the database needs to be upgraded; otherwise, false.|  
|`secretServer`|Returns a string containing the name of the secret server of the database.|  
|`ssoAdminAccount`|Returns a string containing the name of the SSO administration account.|  
|`ssoAffilateAdminAccount`|Returns a string containing the SSO affiliate administration account.|  
  
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
