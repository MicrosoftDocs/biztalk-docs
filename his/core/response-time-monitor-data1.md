---
title: "Response Time Monitor Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e79b1f42-7f17-48cc-a58a-d5307450f3cc
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Response Time Monitor Data
For a 3270 display application, the local node maintains statistics on host response times—the time it takes the host to respond after the 3270 user presses ENTER or an AID key to send data to the host. These statistics can then be sent to the host for analysis.  
  
 The [Status-RTM](./status-rtm1.md) message, sent by the local node to the application, informs the application of the Response Time Monitor (RTM) parameters specified by the host. (For more information, see [RTM Parameters](../core/rtm-parameters]2.md).) These parameters specify whether RTM data is to be collected, whether the application is permitted to display RTM statistics locally, the time boundaries by which response times are to be grouped, and the definition of response time. The time can be measured until the first character of the host response reaches the screen, until the keyboard is unlocked, or until the user can send further data (change direction (CD) or end bracket (EB) received by the application).  
  
 If the host specifies that response times are to be measured for this session, the application is responsible for measuring response times and for reporting them to the local node. This involves:  
  
- Starting a timer when the user presses the ENTER key or an AID key to send data to the host.  
  
- Stopping the timer when the host's response to the inbound data is received, as defined by the RTM definition specified on the **Status-RTM** message.  
  
- Reporting the response time to the host on the [Status-Acknowledge(Ack)](./status-acknowledge-ack-2.md) message, which acknowledges the host's response. One of the fields on this message specifies the last response time measured by the application, or specifies that no response time is to be reported.  
  
- Optionally displaying the most recent response time as a last transaction time indicator (LTTI) on the 3270 emulation status line.  
  
  If the application wants to provide a local display of RTM data, it is responsible for maintaining its own response time statistics. It should use the same definition and boundaries as those specified on the [Status-RTM](./status-rtm1.md) message to ensure that the local data matches the data sent to the host by the local node. Note that the **Status-RTM** message can indicate that a local display of response times is not permitted. In this case, the application should not display either the response times or the LTTI.  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
 [Closing the PLU Connection](../core/closing-the-plu-connection1.md)   
 [PLU Session](../core/plu-session2.md)   
 [Outbound Chaining](../core/outbound-chaining2.md)   
 [Inbound Chaining](../core/inbound-chaining1.md)   
 [Segment Delivery](../core/segment-delivery1.md)   
 [Brackets](../core/brackets1.md)   
 [Direction](../core/direction1.md)   
 [Pacing and Chunking](../core/pacing-and-chunking1.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data]1.md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce1.md)   
 [Recovery](../core/recovery1.md)   
 [Application-Initiated Termination](../core/application-initiated-termination1.md)   
 [LUSTATs\]](../core/lustats]1.md)