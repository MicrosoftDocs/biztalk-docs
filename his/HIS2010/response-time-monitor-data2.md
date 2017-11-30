---
title: "Response Time Monitor Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c5cfa37-110a-4758-a79f-b89edb165150
caps.latest.revision: 3
---
# Response Time Monitor Data
For a 3270 display application, the local node maintains statistics on host response times—the time it takes the host to respond after the 3270 user presses ENTER or an AID key to send data to the host. These statistics can then be sent to the host for analysis.  
  
 The [Status-RTM](../HIS2010/status-rtm2.md) message, sent by the local node to the application, informs the application of the Response Time Monitor (RTM) parameters specified by the host. (For more information, see [RTM Parameters](../HIS2010/rtm-parameters]1.md).) These parameters specify whether RTM data is to be collected, whether the application is permitted to display RTM statistics locally, the time boundaries by which response times are to be grouped, and the definition of response time. The time can be measured until the first character of the host response reaches the screen, until the keyboard is unlocked, or until the user can send further data (change direction (CD) or end bracket (EB) received by the application).  
  
 If the host specifies that response times are to be measured for this session, the application is responsible for measuring response times and for reporting them to the local node. This involves:  
  
-   Starting a timer when the user presses the ENTER key or an AID key to send data to the host.  
  
-   Stopping the timer when the host's response to the inbound data is received, as defined by the RTM definition specified on the **Status-RTM** message.  
  
-   Reporting the response time to the host on the [Status-Acknowledge(Ack)](../HIS2010/status-acknowledge-ack-1.md) message, which acknowledges the host's response. One of the fields on this message specifies the last response time measured by the application, or specifies that no response time is to be reported.  
  
-   Optionally displaying the most recent response time as a last transaction time indicator (LTTI) on the 3270 emulation status line.  
  
 If the application wants to provide a local display of RTM data, it is responsible for maintaining its own response time statistics. It should use the same definition and boundaries as those specified on the [Status-RTM](../HIS2010/status-rtm2.md) message to ensure that the local data matches the data sent to the host by the local node. Note that the **Status-RTM** message can indicate that a local display of response times is not permitted. In this case, the application should not display either the response times or the LTTI.  
  
## See Also  
 [Opening the PLU Connection](../HIS2010/opening-the-plu-connection2.md)   
 [Closing the PLU Connection](../HIS2010/closing-the-plu-connection2.md)   
 [PLU Session](../HIS2010/plu-session1.md)   
 [Outbound Chaining](../HIS2010/outbound-chaining1.md)   
 [Inbound Chaining](../HIS2010/inbound-chaining2.md)   
 [Segment Delivery](../HIS2010/segment-delivery2.md)   
 [Brackets](../HIS2010/brackets2.md)   
 [Direction](../HIS2010/direction2.md)   
 [Pacing and Chunking](../HIS2010/pacing-and-chunking2.md)   
 [Confirmation and Rejection of Data\]](../HIS2010/confirmation-and-rejection-of-data]2.md)   
 [Shutdown and Quiesce](../HIS2010/shutdown-and-quiesce2.md)   
 [Recovery](../HIS2010/recovery2.md)   
 [Application-Initiated Termination](../HIS2010/application-initiated-termination2.md)   
 [LUSTATs\]](../HIS2010/lustats]2.md)