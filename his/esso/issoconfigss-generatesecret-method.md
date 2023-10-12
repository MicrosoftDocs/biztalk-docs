---
description: "Learn more about: ISSOConfigSS.GenerateSecret Method"
title: "ISSOConfigSS.GenerateSecret Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOConfigSS.GenerateSecret Method
The **GenerateSecret** method generates the secret for the secret server.  
  
## Syntax  
  
```vb  
  
GenerateSecret(  
backupFile As String,   
filePassword As String,   
filePasswordReminder As String  
);  
  
```  
  
```cpp#  
  
HRESULT GenerateSecret(  
BSTR backupFile,   
BSTR filePassword,   
BSTR filePasswordReminder  
);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`backupFile`|String containing the path and name of the backup file for the secret server.|  
|`filePassword`|String containing the backup file password.|  
|`filePasswordReminder`|String containing the secret server file password reminder|  
  
## Property Value/Return Value  
 [C++] This method returns an HRESULT indicating whether it completed successfully. For more details, see the Error Values section.  
  
 [Visual Basic] Not Applicable.  
  
## Exceptions  
 C++] This method returns an HRESULT containing one of the values in the following table.  
  
 [Visual Basic] This method indicates errors by setting the Number property of the global Err object to one of the values in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDREG|An invalid parameter was detected.|
