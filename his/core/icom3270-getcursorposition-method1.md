---
description: "Learn more about: Icom3270.getCursorPosition Method"
title: "Icom3270.getCursorPosition Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8b793f4-c759-4724-8d75-307be942578e
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.getCursorPosition Method
The getCursorPosition method retrieves the current cursor position as an offset of the 3270 display buffer.  
  
## Syntax  
  
```  
  
void GetCursorPosition(  
   out ushort position  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|When this method returns, contains a 0-based offset describing the current cursor position.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|C3270_E_SESSIONBUSY|The 3270 session is busy.<br /><br /> You may call wait to determine when input is allowed and getCurrentPosition can be retried.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 The cursor position may change as a result of a call to setCursorPosition, sendKey, or wait.
