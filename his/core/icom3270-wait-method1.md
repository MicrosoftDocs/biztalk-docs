---
title: "Icom3270.wait Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae52225c-73ea-452c-ac27-f36ebc62ca24
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Icom3270.wait Method
The wait method waits for the session to enter a state where input is allowed or the screen is modified.  
  
## Syntax  
  
```  
  
void Wait(  
   uint howLong,  
   int waitForUpdate  
)  
```  
  
#### Parameters  
  
|Parameters|Value|  
|----------------|-----------|  
|`howLong`|A period of time, measured in units of 0.5 seconds, that the thread is willing to waif for input to be enabled or the screen to be updated. 0xffffffff indicates that the thread should wait indefinitely.|  
|`waitForUpdate`|If false, this method will return as soon as the session is in an input allowed state.<br /><br /> The session returns immediately if the session is currently in an input allowed state.<br /><br /> For more information, see the Remarks section.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The session is available for input.|  
|C3270_S_SIZECHANGED|The session is available for input, but the screen size was modified during the invocation of wait.  You should gall getScreenSize to determine the new screen size.|  
|C3270_E_SESSIONBUSY|The 3270 session is still busy, but the time-out period specified by howLong expired.<br /><br /> You should perform any necessary processing before calling wait again.|  
|C3270_E_SESSSIONLOCKED|The 3270 session is locked due to a local lock condition.<br /><br /> You should examine the OIA buffer to determine the reason for the error. You may also send a RESET keystroke to unlock the keyboard before calling wait again or performing any other recovery action.|  
|C3270_E_SESSIONFAILURE|The 3270 session failed. Either the PLU_SLU or SSCP session was deactivated while the wait was in progress.<br /><br /> You should examine the session status in the OIA for the session and take appropriate recovery action.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
  
## Remarks  
 Calling wait allows the session to process messages from the host when the application is active, connected to the host, and waiting for data.  
  
 You should set waitForUpdate to true when the Host unlocks the keyboard and sends screen updates in separate operations. In particular, you should do this on the SSCP session, where input is enabled on receipt of an SNA response to data from the client. The reply data is dent on a subsequent message.