---
title: "ISSOConfigSS.GenerateSecret Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d030cba-2a35-4dcc-919b-53ca0b344e50
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
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