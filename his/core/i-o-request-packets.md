---
title: "I-O Request Packets1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3676638-c7e8-495f-91a6-ee5a44f08d68
caps.latest.revision: 3
---
# I/O Request Packets
All I/O requests are passed to the driver by Microsoft Windows using the standard IRP structure. For more details about this, refer to the Windows Device Driver Kit.  
  
 I/O request packets are defined in terms of C structures. The relevant fields are accessed as follows:  
  
|Field name|Description|  
|----------------|-----------------|  
|IRP.CurrentStackLocation -> MajorFunction|Defines the IRP as an IOCTL.|  
|IRP.IoStatus|Status codes upon completion of request.|  
|IRP.CurrentStackLocation -> IoControlCode|The IOCTL function code.|  
  
 **IoControlCode** identifies the function to be performed and **IoStatus** is the mechanism for returning result codes to the SNALink. The structure **IoStatus** is defined as follows:  
  
 **IoStatus.Status**  
 A standard Windows result code (for example, STATUS_INVALID_PARAMETER) as defined in the Windows header file NTSTATUS.H.  
  
 **IoStatus.Information**  
 For successful read-frame IOCTLs, the length of the received buffer (can be zero if no data available). Additional error information, as defined in the header file SECLINK.H.  
  
## In This Section  
  
-   [Initialization](../core/initialization-i-o-request-packets.md)  
  
-   [OPEN Call](../core/open-call.md)  
  
-   [CLOSE Call](../core/close-call.md)  
  
-   [IOCTL Command Summary](../core/ioctl-command-summary.md)  
  
-   [Equates and Structure Layouts](../core/equates-and-structure-layouts.md)