---
title: "Maximum Buffer Sizes for Remote Environments2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac05c5aa-5ecd-4138-baa2-6b07797fe3e0
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Maximum Buffer Sizes for Remote Environments
Both Transaction Integrator (TI) and mainframe applications must be designed not to exceed the following buffer size or transfer limitations:  
  
## TCP Transaction Request Message (TRM) Link  
 The maximum buffer size for input/output is 32767 bytes. This limit is defined by the maximum allowable size of the COMMAREA.  
  
## TCP Enhanced Listener Message (ELM) Link  
 The maximum buffer size for input/output is 32767 bytes. This limit is defined by the maximum allowable size of the COMMAREA.  
  
## TCP Transaction Request Message (TRM) User Data  
 The buffer size for input/output is unlimited.  
  
## TCP Enhanced Listener Message (ELM) User Data  
 The buffer size for input/output is unlimited.  
  
## IMS Connect (TCP/IP)  
 The maximum segment size that TI can send to IMS is 32754 bytes. This limit is defined by the total number of bytes (32767) in an IMS message segment minus the following number of bytes:  
  
- 2 bytes for the LL (Length field).  
  
- 2 bytes for the ZZ (Control Information field).  
  
- 9 bytes for the maximum TRANCODE.  
  
  The total amount of data that can be sent to, or received from, an IMS server program using the TCP/IP IMS Connect programming model is unlimited.  
  
## OS/400 Distributed Program Calls (DPC)  
 The total buffer size is 65535 bytes and is reduced by the required headers. The send requires 23 bytes of header.  
  
 Each parameter, of either direction, requires 12 bytes of overhead on the send.  Each in\out or out parameter requires 12 bytes of overhead within memory on the return trip.  
  
## CICS LINK LU 6.2  
 The maximum buffer size for input/output is 32767 bytes. This limit is defined by the maximum allowable size of the COMMAREA.  
  
## CICS User Data LU 6.2  
 The buffer size for input/output is unlimited. However, if the size of the input buffer is greater than 32 KB, TI sends the data in multiple chunks of 32 KB. In such a case, the mainframe application must do multiple receives to gather all the input data.  
  
## IMS Using LU 6.2  
 The maximum segment size that TI will send to IMS is 32754 bytes. This limit is defined by the total number of bytes (32767) in an IMS message segment minus the following number of bytes:  
  
- 2 bytes for the LL (Length field).  
  
- 2 bytes for the ZZ (Control Information field).  
  
- 9 bytes for the maximum TRANCODE.  
  
  The total amount of data that can be sent to, or received from, an IMS server program that uses LU 6.2 is unlimited.  
  
## See Also  
 [Host and Automation Data](../core/host-and-automation-data1.md)