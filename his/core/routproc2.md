---
title: "routproc2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f756842-46e8-4437-b1d4-091dc8aa1f8f
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# routproc
The **routproc** function is a sample routing procedure. It must be supplied as part of the application. It is called by the Dynamic Access Module (DMOD) with a message that may or may not be for this application The DMOD calls routing procedures in turn until one accepts the message.  
  
## Syntax  
  
```  
  
DWORD routproc(   
BUFHDR *msgptr,   
USHORT locl,   
USHORT retstat   
);  
```  
  
#### Parameters  
 *msgptr*  
 Pointer to the message passed by the DMOD to the routing procedure.  
  
 *locl*  
 Locality from which message was received (if *retstat* indicates message returned), or locality to which path was lost (if *retstat* indicates path error).  
  
 *retstat*  
 Reason for call:  
  
 CEDINMSG (1)—message returned.  
  
 CEDINLLN (2)—path error (see Remarks below).  
  
## Return Value  
 TRUE  
 The routing procedure has accepted the message.  
  
 FALSE  
 The message is not for this routing procedure.  
  
## Remarks  
 The routing procedure should first call [sbpurcvx](../core/sbpurcvx1.md), which handles any Open response messages, as follows:  
  
 <strong>sbpurcvx(</strong>&*msgptr*, *locl*, <em>retstat</em>**)**  
  
 A return code of TRUE from **sbpurcvx** indicates that **sbpurcvx** has accepted the message; an Open error response has been received for this application, and resource location is continuing. The routing procedure should not process the message any further and should return **TRUE** to prevent the DMOD from calling further routing procedures.  
  
 A return code of **FALSE** from **sbpurcvx** indicates that the routing procedure should:  
  
- If the message is for this application, take responsibility for the message and return **TRUE** to prevent the DMOD from calling further routing procedures.  
  
- If the message is not for this application, return **FALSE** so that the DMOD tries further routing procedures.  
  
  If a path error is returned, *msgptr* will not point to a valid message, and no more function management interface (FMI) messages will be returned for the locality value indicated. The application is responsible for ending all sessions using this locality. The routing procedure must return **FALSE**. This ensures that the lost locality is reported to all other routing procedures.  
  
  If the message is for this application, the routing procedure can either process the message immediately or put the message on an application queue, and then post the application using a semaphore. For more information, see [Receiving Messages](./receiving-messages1.md).