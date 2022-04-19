---
description: "Learn more about: Icom3270.setScreenData Method"
title: "Icom3270.setScreenData Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec3db1a8-977e-4cd7-a19e-50c4dfff15f4
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.setScreenData Method
The `setScreenData` method copies data characters, character attributes, and extended attributers to all or part of the screen.  
  
## Syntax  
  
```  
  
void SetScreenData(  
   ushort position,  
   ushort length,  
   int overwriteProtected,  
   ref System.Array dbuf,  
   ref System.Array abuf,  
   ref System.Array eabuf  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`position`|The 0-based screen offset of the screen position to start copying.|  
|`length`|The length of the data to search on.|  
|`overwriteProtected`|true to allow the application to write data to a protected field; otherwise attempting to write to a protected field will cause an error.|  
|`dbuf`|The data to copy to the screen data buffer data. NULL indicates that you do not want to alter the data buffer.|  
|`abuf`|The data to copy to the screen character attribute buffer data. NULL indicates that you do not want to alter the character attribute buffer.|  
|`eabuf`|When this method returns, contains the data to copy to the screen extended attribute buffer data. NULL indicates that you do not want to alter the extended attribute buffer.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully|  
|C3270_E_TRUNCATED|The copy extended past the end of the buffer screen. The extra data was ignored.|  
|C3270_E_INVALIDPOS|The specified screen position is greater than the maximum character position for the current screen size.|  
|C3270_E_INVALIDDATA|The bounds of any non-NULL SAFEARRAY parameters were not identical.|  
|C3270_E_SESSIONBUSY|The 3270 session was busy.<br /><br /> You should call Icom3270.wait to determine when input is allowed and this method can be retried.|  
|C3270_E_SESSIONLOCKED|The 3270 session is locked to a local lock condition. You should examine the OIA buffer to determine the reason for the lock. You may also send a RESET keystroke to unlock the keyboard before calling this method again.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks
