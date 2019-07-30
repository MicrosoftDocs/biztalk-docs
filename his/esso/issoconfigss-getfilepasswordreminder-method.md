---
title: "ISSOConfigSS.GetFilePasswordReminder Method | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a13b8194-1b43-4125-9a41-dbb981e6e896
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
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