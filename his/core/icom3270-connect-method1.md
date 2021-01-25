---
description: "Learn more about: Icom3270.connect Method"
title: "Icom3270.connect Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 828a297c-7bb6-47a2-aa1e-3aa558c92318
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Icom3270.connect Method
The connect method connects a com3270 client to an existing session.  
  
## Syntax  
  
```  
  
void Connect(  
   object sessionHandle  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`sessionHandle`|Session handle of the session to connect to.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method completed successfully.|  
|C3270_E_ALREADY_CONNECTED|Another com3270 client is connected to the specified session.|  
|C3270_E_SYSERROR|The method failed due to an internal error.|  
|E_NOINTERFACE|The specified session handle is not a valid comSNA3270, COMTN3270, or comLocal3270 IUnknown interface pointer.|  
  
## Exceptions  
  
## Remarks  
 Once you connect successfully to a session, you are responsible for calling Icom3270.wait in order to provide processing time for incoming 3270 data stream packets.  
  
 You are guaranteed exclusive access to the session until you call disconnect. Specifically, the screen buffers and screen size are guarnenteed not to change unless you call Icom3270.wait.  
  
 If connect completes successfully, you should then call Icom3270.wait. Calling wait allows you to process any unprocessed 3270 data and to ensure that the session is in an unlocked state. After calling wait, you can then update or read the display buffers or send keystrokes to the host application.
