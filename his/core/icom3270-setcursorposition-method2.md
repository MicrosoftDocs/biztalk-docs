---
title: "Icom3270.setCursorPosition Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b59b46b-3231-4025-b9bf-155fd9097d90
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.setCursorPosition Method
The setCursorPosition sets the position of the cursor on the 3270 screen.  
  
## Syntax  
  
```  
  
void SetCursorPosition(  
   ushort position  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`pos`|A 0-based offset within the screen buffer that describes the location of the cursor.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_SESSIONBUSY|The 3270 session is busy.<br /><br /> You may call Icom3270.wait to determine when input is allowed. Afterwards, you can attempt to call setCursorPosition again.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 After you call setCursor, you may call sendKey. Calling sendKey will write printable character, starting from the location specified by setCursor.  
  
 To determine the offset of a particular row and column character address, you can use getScreenSize to retrieve the number of columns in each screen row.