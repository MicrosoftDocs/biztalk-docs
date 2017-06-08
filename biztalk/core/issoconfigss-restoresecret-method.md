---
title: "ISSOConfigSS.RestoreSecret Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b5dabed-0b56-4aad-9e2c-228a0c044638
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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