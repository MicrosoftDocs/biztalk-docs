---
title: "IcomLUO.Offline Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5136891-0bc4-4772-a37c-e24e01371282
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IcomLUO.Offline Method
Switches the LU0 session into an off-line state, which in turn causes the underlying SNA session to deactivate.  
  
## Syntax  
  
```  
  
void Offline()  
```  
  
#### Parameters  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The session has been successfully deactivated.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for this comLU0 method, which has not yet returned.|  
|CLU_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> The application should release the session handle.|  
|CLU0_E_RECEIVE_IN_PROGRESS|The application has not yet completed receiving the last chain sent by the host. This may be indicated by Receive returning DATA_INCOMPLETE.<br /><br /> You should re-issue the IcomLU0.Receive call to collect the remaining data, and then call IcomLU0.Offline again.|  
|CLU0_E_SYSERROR|This method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 After calling Offline, the client application can later reactivate the session using a call to Online.  
  
 Note that Offline releases the SNA server LU. Therefore, it is possible for another application to acquire the LU before your application calls Online again.  
  
 You can use Online to recover a session that has returned CLU0_E_SESSION_FAILED.