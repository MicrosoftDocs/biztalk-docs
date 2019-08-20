---
title: "sepdrout2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d496c00c-074b-48b6-9fbb-b0038c2e30ab
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# sepdrout
The **sepdrout** function for Win32® allows an application to perform its own routing of received messages by setting up a procedure that is called by the Dynamic Access Module (DMOD) when a message is received.  
  
## Syntax  
  
```  
  
DWORD sepdrout(  
DWORD ( *proc_addr,)  
(BUFHDR *, USHORT, USHORT  
);  
  
DWORD sepdrout(   
    DWORD *proc_addr,   
    (BUFHDR *, USHORT, USHORT   
   );  
```  
  
#### Parameters  
 *proc_addr*  
 The routing procedure.  
  
## Return Value  
 NO_ERROR (0)  
 Successful.  
  
 Anything else  
 Unsuccessful.  
  
## Remarks  
 This facility is only available to clients, as defined in the call to [sbpuinit](../core/sbpuinit1.md).  
  
 An application can have up to four routing procedures. Note that the Advanced Program-to-Program Communications (APPC) and Common Service Verb (CSV) libraries each use a routing procedure. When the DMOD receives a message, each routing procedure is called, until one accepts the message.  
  
 For an example of a routing procedure, see [routproc](../core/routproc2.md).