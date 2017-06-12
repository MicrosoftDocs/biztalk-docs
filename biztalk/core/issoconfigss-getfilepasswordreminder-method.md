---
title: "ISSOConfigSS.GetFilePasswordReminder Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71833ea3-a19f-431b-b8a1-96355113d171
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ISSOConfigSS.GetFilePasswordReminder Method
The **GetFilePasswordReminder** method gets the password reminder from the backup file.  
  
## Syntax  
  
```vb  
  
Function GetFilePasswordReminder(  
restoreFile as String);  
```  
  
```csharp  
  
void GetFilePasswordReminder(  
string restoreFile,  
out string filePasswordReminder);  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`restoreFile`|The file from which the reminder is to be retrieved.|  
|`filePasswordReminder`|The reminder for the file password.|  
  
## Property Value/Return Value  
 [Visual Basic] The file password reminder.  
  
## Remarks  
 This function goes directly to the restore file to get the password reminder, hence the user must have read access to the restore file.