---
title: "ISSOConfigSS.RestoreSecret Method | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5cca54e-330e-4b2c-94c7-57f789af7a63
caps.latest.revision: 3
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