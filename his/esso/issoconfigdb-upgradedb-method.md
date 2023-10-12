---
description: "Learn more about: ISSOConfigDB.UpgradeDB Method"
title: "ISSOConfigDB.UpgradeDB Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOConfigDB.UpgradeDB Method
The UpgradeDatabase method upgrades the specified Single Sign-On (SSO) database to SSO version 3.  
  
## Syntax  
  
```vb  
  
Sub UpgradeDB (  
sqlServer As String,   
sqlDatabase As String  
);  
```  
  
```cpp#  
  
HRESULT UpgradeDB (  
BSTR sqlServer,   
BSTR sqlDatabase  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`sqlServer`|String containing the SQL server in which the database exists.|  
|`sqlDatabase`|String containing the name of the database.|  
  
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
