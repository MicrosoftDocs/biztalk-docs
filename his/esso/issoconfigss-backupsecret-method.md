---
title: "ISSOConfigSS.BackupSecret Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dc8c495-7ff1-4ed0-921a-0828e69319b8
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ISSOConfigSS.BackupSecret Method
The **BackupSecret** method backs up the secret server.  
  
## Syntax  
  
```vb  
  
backupFile As String,   
filePassword As String,   
filePasswordReminder As String  
);  
```  
  
```cpp#  
  
BSTR backupFile,   
BSTR filePassword,   
BSTR filePasswordReminder  
);  
  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`backupFile`|String containing the path and name of the secret server backup file.|  
|`filePassword`|String containing the backup file password.|  
|`filePasswordReminder`|String containing the secret server file password reminder.|  
  
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