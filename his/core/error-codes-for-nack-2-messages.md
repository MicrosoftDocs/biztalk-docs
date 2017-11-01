---
title: "Error Codes for Nack-2 Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05aed1e0-70d2-439f-bed4-6960be87aa92
caps.latest.revision: 3
---
# Error Codes for Nack-2 Messages
The possible error codes delivered to the function management interface (FMI) application on [Status-Acknowledge(Nack-2)](../Topic/Status-Acknowledge\(Nack-2\)1.md) and [Status-Control(...) Negative-Acknowledge-2](../Topic/Status-Control\(...\)%20Negative-Acknowledge-22.md) messages are tabulated in the following table. A **Nack-2** is delivered to the application in response to data that is sent in error (or a [Status-Control(...) Request](../Topic/Status-Control\(...\)%20Request1.md) that is in error). The data has not been sent to the host. The table indicates whether the error is critical, applying to the primary logical unit (PLU) connection only. If the error is critical, the critical failure indicator will be set in the message, and the application will receive a [Close(PLU) Request](../Topic/Close\(PLU\)%20Request1.md) as the next message.  
  
 **All Nack-2** messages have the second word of information as 0x0000.  
  
|Error /<br /><br /> Sense code|Critical<br /><br /> YES/NO|Description|  
|-----------------------------|--------------------------|-----------------|  
|0x0040|YES|No buffer element on DATAFMI message.|  
|0x0042|YES|DATAFMI message sent when no credit.|  
|0x0043|YES|Invalid status-control for Transmission Service profile (TS profile).|  
|0x0044|YES|Invalid status-control from application.|  
|0x004A|YES|Half-duplex (HDX) contention and -QR,-BB,EB, or BKTFSM in pending-term-session.|  
|0x0809|YES|Mode inconsistency.|  
|0x1002|YES|Request/response unit (RU) length error.|  
|0x1003|YES|Function not supported, invalid function management (FM) profile.|  
|0x2002|NO|Chaining error.|  
|0x2003|NO|Bracket error.|  
|0x2004|NO|Direction error.|  
|0x2005|YES|Data traffic reset.|  
|0x2006|YES|Data traffic quiesced.|  
|0x200D|YES|Response owed before sending request (half-duplex).|  
|0x4003|YES|Begin bracket (BB) not allowed.|  
|0x4004|YES|End bracket (EB) not allowed.|  
|0x4006|YES|Exception response not allowed.|  
|0x4007|YES|Definite response not allowed.|  
|0x4009|YES|Change direction (CD) not allowed.|  
|0x400A|YES|No-response not allowed.|  
|0x400B|YES|Chaining not supported.|  
|0x400C|YES|Brackets not supported.|  
|0x400D|YES|CD not supported.|  
|0x400F|YES|Incorrect use of FI.|  
|0x4014|YES|Incorrect use of DR1, DR2, ER.|  
|0x8005|NO|System services control point (SSCP) data sent when logical unit (LU) inactive.|