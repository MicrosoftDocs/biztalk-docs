---
description: "Learn more about: ISSOConfigSS.GetFilePasswordReminder Method"
title: "ISSOConfigSS.GetFilePasswordReminder Method"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
