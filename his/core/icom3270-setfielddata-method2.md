---
title: "Icom3270.setFieldData Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c3b6070-a1b6-4d63-9444-6ab53a3f1ea0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Icom3270.setFieldData Method
The setFieldData method sets the data contents of the specified field.  
  
## Syntax  
  
```  
  
void SetFieldData(  
   ushort position,  
   ushort length,  
   int overwriteProtected,  
   ref System.Array dbuf,  
   ref System.Array abuf,  
   ref System.Array eabuf  
)  
```  
  
#### Parameters  
  
|Parameter|Value|  
|---------------|-----------|  
|`position`|The 0-based screen offset of a character in the desired field.|  
|`length`|The length of the data to copy.|  
|`overwriteProtected`|If true, allows you to write data to a protected file. Otherwise, attempting to write to a protected field will cause an error.|  
|`dbuf`|The data to copy to the screen data buffer data. NULL indicates that you do not want to alter the screen data.|  
|`abuf`|The data to copy to the screen character attribute buffer data. NULL indicates that you do not want to alter the character attribute buffer.|  
|`eabuf`|When this method returns, contains the data to copy to the screen extended attribute buffer data. NULL indicates that you do not want to alter the extended attribute buffer.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|C3270_S_TRUNCATED|The copy extended past the end of the field. Therefore, the extra data was ignored.|  
|C3270_E_INVALIDPOS|The screen position specified is greated than the maximum character position for the current screen size.|  
|C3270_E_INVALIDDATA|The bounds of any of the non-NULL SAFEARRA parameters were not identical.|  
|C3270_E_UNFORMATTED|The screen is unformatted. As such, the specified field does not exist.|  
|C3270_E_SESSIONBUSY|The 3270 session is busy. Call Icom3270.wait to determine when input is allowed so that you may call this method again.|  
|C3270_E_SESSIONLOCKED|The 3270 session is loced due to a local lock condition. Examine the OIA buffer to determine the reason for the error. Also, you may also send a RESET keystroke to unlock the keyboard before calling this method or taking any other recovery action.|  
|C3270_E_NOTCONNECTED|The com3270 client is not connected to a session through a call to Icom3270.connect.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 You cannot use setFieldData to modify the Field attribute character.  
  
 For the purpose of setFieldData, the field attribute character is considered part of the field. The field attribute character immediately precedes the field data.