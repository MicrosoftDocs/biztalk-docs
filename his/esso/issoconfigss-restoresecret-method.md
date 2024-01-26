---
description: "Learn more about: ISSOConfigSS.RestoreSecret Method"
title: "ISSOConfigSS.RestoreSecret Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ISSOConfigSS.RestoreSecret Method
The **RestoreSecret** method restores master secrets from the password protected backup file.  
  
## Syntax  
  
```vb  
  
Sub RestoreSecret(  
restoreFile as String,  
filePassword as String);  
```  
  
```csharp  
  
void RestoreSecret(  
string restoreFile,  
string filePassword);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`restoreFile`|The file from which the secrets are to be restored.|  
|`filePasswordReminder`|The password used to protect the restore file.|
