---
title: "sbpuinit1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7e4f07d-4776-49dc-acfc-5f0e9173e3af
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
---
# sbpuinit
The **sbpuinit** function initializes the DL-BASE.  
  
## Syntax  
  
```  
  
USHORT sbpuinit(   
HANDLE *sema4ptr,   
USHORT proctype,   
USHORT servtype,   
UCHAR *uname   
);  
```  
  
#### Parameters  
 *sema4ptr*  
 Semaphore, created by Dynamic Access Module (DMOD), cleared by DMOD when a message is available. This address is for internal use by [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)]. The application should not subsequently attempt to reference the address.  
  
 *proctype*  
 Type of process: CLIENT–2.  
  
 *servtype*  
 Type of service/client: CES3270–2.  
  
 *uname*  
 Pointer to a character buffer of length at least 21 characters; the LAN Manager user name, or other identifying name appropriate to the network operating system, is returned to the application in this buffer. The application does not need to use this parameter, but can use it for display or logging.  
  
## Return Value  
 NO_ERROR  
 Initialization successful.  
  
 Any other return value indicates that the initialization failed. This is usually an operating system return code. The following values are also used:  
  
 DMLTABF (555)  
 L table is full.  
  
 DMMNWGI (562)  
 Failed to get network operating system information.  
  
 DMDSTFL (563)  
 Service table is full.  
  
 DMMPIPF (567)  
 Failed to make a named pipe.  
  
 DMCOMNM (582)  
 No name registered for this application.  
  
 DMCOMDUP (596)  
 A service is already running with the same name.  
  
 DMNOTLOG (598)  
 User is not logged on to network operating system.  
  
 DMCFGOPN (616)  
 Failed to open configuration file.  
  
 DMCFGREAD (618)  
 Failed to read from configuration file.  
  
 DMNONAP (625)  
 The Network Access Program (NAP) is not started.  
  
 DMMAXAPP (953)  
 Windows only: Maximum number of concurrent applications exceeded.  
  
## Remarks  
 The **sbpuinit** entry point should always be called before any other DL-BASE or DMOD entry points except [SNAGetVersion](../core/snagetversion.md). For new emulators, [sepdcrec](../core/sepdcrec.md) should be called after **sbpuinit**. (Because of the order of calls used in older emulators, a call to **sepdcrec** before **sbpuinit** is still supported, but this order is not recommended.)