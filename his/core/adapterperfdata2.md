---
title: "ADAPTERPERFDATA2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21c956b2-7fec-40c1-a6d8-f026a8c9897e
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# ADAPTERPERFDATA
The **ADAPTERPERFDATA** structure groups all of the [ADAPTERCOUNTER](../core/adaptercounter2.md) structures for an SNA link service together into a single block. It also has a few fields used internally by the SNA Perfmon code. The SNA link driver should not change the first three members of this structure.  
  
## Syntax  
  
```  
  
typedef struct adapterperfdata  
{  
    ULONG inuse;  
    ULONG ServiceNameIndex;  
    ULONG FirstCounterIndex;  
    ADAPTERCOUNTER TotalBytesReceived;  
    ADAPTERCOUNTER TotalBytesTransmitted;  
    ADAPTERCOUNTER TotalFramesReceived;  
    ADAPTERCOUNTER TotalFramesTransmitted;  
    ADAPTERCOUNTER SuccessfulConnects;  
    ADAPTERCOUNTER ConnectionFailures;  
    ADAPTERCOUNTER TotalBytesThroughput;  
    ADAPTERCOUNTER TotalFramesThroughput;  
    ADAPTERCOUNTER AdapterFailures;  
    ADAPTERCOUNTER reserved[11];  
    ULONG pad;  
} ADAPTERPERFDATA;  
```  
  
## Members  
 **inuse**  
 A flag that indicates that the link service is using this section of shared memory.  
  
 **ServiceNameIndex**  
 An index into an array of strings describing events that can be monitored by the Perfmon functions. These strings are stored in the registry under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Perflib key.  
  
 **FirstCounterIndex**  
 An index into an array of events that can be monitored by the Perfmon functions.  
  
 **TotalBytesReceived**  
 The number of data bytes received per second.  
  
 **TotalBytesTransmitted**  
 The number of data bytes transmitted per second.  
  
 **TotalFramesReceived**  
 The number of data frames received per second. A frame is an information structure recognized by one of the various protocols related to SNA. Frames contain multiple bytes of data.  
  
 **TotalFramesTransmitted**  
 The number of data frames transmitted per second.  
  
 **SuccessfulConnects**  
 The number of times since startup that a successful connection has been made.  
  
 **ConnectionFailures**  
 The number of times since startup that a connection has encountered an error condition.  
  
 **TotalBytesThroughput**  
 The total number of bytes flowing through Host Integration Server per second. This includes both incoming and outgoing bytes, and is a good indicator of how heavily your Host Integration Server is loaded.  
  
 **TotalFramesThroughput**  
 The total number of data frames flowing through Host Integration Server per second. This includes both incoming and outgoing frames, and is a good indicator of how heavily your Host Integration Server is loaded.  
  
 **AdapterFailures**  
 The number of times since startup that a network adapter has encountered an error condition.  
  
 **reserved**  
 An array of **ADAPTERCOUNTER** structures for future expansion.  
  
 **pad**  
 Padding.