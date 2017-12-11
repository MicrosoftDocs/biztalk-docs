---
title: "sepdcrec1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d8c2148-7e61-45f5-b167-7614a365a6b6
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# sepdcrec
The **sepdcrec** function gets configuration information. The application calls this function to obtain the 3270 configuration information for the name with which the user logged on to the network operating system. The call also registers this user name in the service table.  
  
## Syntax  
  
```  
  
USHORT sepdcrec(   
UCHAR *pBuffer,  
USHORT length,  
USHORT *numbytes  
);  
```  
  
#### Parameters  
 *pBuffer*  
 Pointer to a buffer supplied by the application, in which configuration information is returned.  
  
 *length*  
 Size of the supplied buffer.  
  
 *numbytes*  
 Used by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] to return the number of bytes of information returned in the buffer.  
  
## Return Value  
 NO_ERROR (0)  
 OK.  
  
 NOCSSRVR (1)  
 No configuration file server available.  
  
 NODGNREC (2)  
 No diagnostics record found in configuration file.  
  
 NOUSRREC (3)  
 No user record found in configuration file for this user.  
  
 BUF2SMAL (4)  
 Supplied buffer was too small.  
  
 NONOS (5)  
 Network operating system is not started.  
  
 NOTLOGON (6)  
 User is not logged on to the network operating system.  
  
 READERR (7)  
 Failed to read from configuration file.  
  
 NONAP (8)  
 The Network Access Program (NAP) is not started.  
  
 MAXAPP (9)  
 Windows only:  Maximum number of concurrent applications exceeded.  
  
 ERROR_SERVER (14)  
 Error on the server end of the remote procedure call (RPC).  
  
 ERROR_LOCAL_FAILURE (15)  
 Error on the local end of the RPC.  
  
## Remarks  
 The [sbpuinit](../core/sbpuinit1.md) function should always be called before any other DL-BASE or Dynamic Access Module (DMOD) entry points except [SNAGetVersion](../core/snagetversion1.md). For new emulators, **sepdcrec** should be called after **sbpuinit**. (Because of the order of calls used in older emulators, a call to **sepdcrec** before **sbpuinit** is still supported, but this order is not recommended.)  
  
 On successful return, the buffer contains pointers to the appropriate 3270 user record and the diagnostics record, followed by the records themselves. It is formatted as follows:  
  
```  
TECWRKUS *pUserRecord,   
TEDIAGNS *pDiagRecord   
);  
```  
  
 (UserRecord—variable length)  
  
 (DiagRecord)  
  
 The two records should be accessed using the supplied pointers.  
  
 See [Configuration Information](../HIS2010/configuration-information2.md) for details of the format of these records and of how the application uses the configuration file information.  
  
 If there is no 3270 user record for this user in the configuration file, or if no diagnostics record is found in the configuration file (an internal error), the application should terminate and not allow the user to use 3270 emulation. The Host Integration Server error log messages COM0438 and COM0437 can be used to report these failures.  
  
 If the supplied buffer is too small for the returned information, the contents of the buffer are undefined and should not be examined, but the *numbytes* parameter will contain the total number of bytes of information available (that is, the size of the two pointers plus the two configuration records). The application should retry with a buffer of at least this size.