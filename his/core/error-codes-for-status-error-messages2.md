---
title: "Error Codes for Status-Error Messages2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60194101-fcd5-4a6b-998b-d2bf675c8018
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Error Codes for Status-Error Messages
The possible error codes delivered to the function management interface (FMI) application on [Status-Error](./status-error1.md) messages are tabulated in the following table. A **Status-Error** message is delivered to the application in one of several cases, as shown in the following list:  
  
- The local node detects an error in a response sent from the application (as a **Status-Acknowledge** or **Status-Control Ack/Nack-1** message).  
  
- The local node detects an error in some data from the host that will not be delivered to the application as an system detected error indicator (SDI) message (such as an expedited flow request).  
  
- The application sends an invalid **Status** message.  
  
  For inbound responses, the **Status-Error** codes have first byte 0x00. When the application is in error, the table indicates whether the error is critical, applying to the primary logical unit (PLU) connection only. If the error is critical, the application will receive a [Close(PLU) Request](./close-plu-request2.md) as the next message.  
  
  The sense codes beginning with 0x40 will only be delivered if the corresponding receive check has been enabled in the connection information control block (CICB) on the [Open(SSCP) Request](./open-sscp-request2.md) from the application.  
  
  Where the sense code is marked with the * symbol, the second word of sense information carries the request code of the expedited flow request that was in error (for example 0x00C9 for SIGNAL).  
  
|Error /<br /><br /> Sense code|Critical<br /><br /> YES/NO|Description|  
|-----------------------------|--------------------------|-----------------|  
|0x0008|NO|Negative response already sent to this chain.|  
|0x0040|YES|Invalid **Status** message from application.|  
|0x0046|YES|Session failure due to correlation table shortage.|  
|0x0050|YES|Invalid sequence number on Status-Ack.|  
|0x0053|YES|Application may not send status control (**STSN**) negative acknowledge if it supports transaction numbers.|  
|0x0056|YES|**Status-Ack** sent when previous RQD chains are outstanding. (For more information, see [Outbound Data](../core/outbound-data1.md).)|  
|0x0801|NO|Message received when pacing count is zero.|  
|0x0805|NO|**BIND** from another PLU when already bound.|  
|0x0809 *|NO|Mode inconsistency (**QEC** or **SHUTD**).|  
|0x0815|NO|**BIND** from same PLU when already bound.|  
|0x0821|NO|Incorrect **ACTLU** type (SSCP connection).|  
|0x1003 *|NO|Wrong profile/network control request/invalid session control message.|  
|0x2005|NO|Data traffic reset.|  
|0x2007|NO|Data traffic not reset (**STSN** after **SDT**).|  
|0x4009 *|NO|Change direction (CD) not allowed.|  
|0x400B *|NO|Chaining not supported.|  
|0x400C *|NO|Brackets not supported.|  
|0x400F *|NO|Incorrect use of FI.|  
|0x4011 *|NO|Incorrect use of request/response unit (RU) category.|  
|0x4014 *|NO|Incorrect use of definite response 1 (DR1), definite response 2 (DR2), exception response (ER).|