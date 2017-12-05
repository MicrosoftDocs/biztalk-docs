---
title: "Icom3270.sendKey Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7479faa-3e0b-4562-a557-0e94210c1b5c
caps.latest.revision: 4
---
# Icom3270.sendKey Method
The sendKey method sends one or more keystrokes to the Host session.  
  
## Syntax  
  
```  
  
void SendKey(  
   ushort count,  
   ref System.Array keys  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`count`|The number of bytes in the buffer.|  
|`keys`|A pointer to the buffer containing the keystrokes to send.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has returned successfully.|  
|C3270_E_BADPARAM|One of the parameters is invalid.|  
|C3270_E_SESSIONBUSY|The 3270 session is busy.<br /><br /> You may call Icom3270.wait to determine when input is allowed before retrying sendKey.|  
|C3270_E_SESSIONLOCKED|The 3270 session is locked due to a local lock condition.<br /><br /> You may examine the OIA buffer to determine the reason for the error. Afterwards, you may want to send a RESET keystroke to unlock the keyboard before calling sendKey again or any other recovery action.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 sendKey emulates a user typing at the 3270 keyboard. You can use sendkey to send3270 functions, such as RESET, INSERT, or TAB, to the session. You can also send both single and double-byte graphic keys to the session.  
  
 Note that if you send an AID key, the host will ignore any subsequent keys in the buffer. As such, the AID key should be the last keystroke you send.  
  
 Graphic keys are represented by their EBCIDIC character balue, or two characters for DBCS in the Host code page. 3270 Function and AID keys are represented by the multi-byte EBCIDIK key codes described in the Microsoft SNA Server Windows HLLAPI Specification.