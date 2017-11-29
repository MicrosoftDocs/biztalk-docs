---
title: "Bracket Termination1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec6f71c-ea29-4337-9b18-a0554be48858
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Bracket Termination
The local node supports bracket termination rule one (conditional) and bracket termination rule two (unconditional), as specified in the **BIND** request. Some sessions only allow bracket termination by one session partner. This is a **BIND** option, supplied in the bind information control block (BICB) on [Open(PLU) OK Confirm](../Topic/Open\(PLU\)%20OConfirm2.md)), and it is the application's responsibility to determine if (and when) it should request bracket termination.  
  
 If an application is allowed by its **BIND** to terminate brackets, it does so by setting the End Bracket Indicator (EBI) application flag in an inbound [Data](../Topic/Data2.md) or **Status-Control(LUSTAT/CHASE/QC/CANCEL)** message. The bracket is only terminated when the application receives a [Status-Session](../Topic/Status-Session1.md) (BETB) from the local node.  
  
 If the host terminates a bracket successfully, the local node sends a **Status-Session(BETB)** to the application. Note that the EBI application flag on outbound messages does not indicate bracket termination, but indicates that the corresponding request/response unit (RU) carried End Bracket (EB). The bracket is only terminated when the application receives **Status-Session(BETB)**.  
  
 Note that if the application queues data, it should also queue **Status-Session(BETB)** messages. They must not be processed as expedited.  
  
 The following two figures illustrate bracket termination protocols between the local node and the application and how those protocols relate to the underlying SNA protocols.  
  
 In the following figure, the application successfully terminates a bracket by sending an EBI data chain when the application's state is in-bracket, which the host accepts. The local node sends a **Status-Session(BETB)** to indicate that the application's state is now between-bracket.  
  
 ![](../core/media/his-32703l.gif "his_32703l")  
Application successfully terminates a bracket by sending an EBI data chain  
  
 In the following figure, the host successfully terminates a bracket by sending an EBI data chain when the application's state is in-bracket, which the application accepts. The local node sends a **Status-Session(BETB)** to indicate that the application's state is now between-bracket.  
  
 ![](../core/media/his-32703la.gif "his_32703la")  
Application successfully terminates a bracket by sending an EBI data chain  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection.md)   
 [PLU Session](../core/plu-session.md)   
 [Outbound Chaining](../core/outbound-chaining.md)   
 [Inbound Chaining](../core/inbound-chaining.md)   
 [Segment Delivery](../core/segment-delivery.md)   
 [Brackets](../core/brackets.md)   
 [Direction](../core/direction.md)   
 [Pacing and Chunking](../core/pacing-and-chunking.md)   
 [Confirmation and Rejection of Data\]](../core/confirmation-and-rejection-of-data].md)   
 [Shutdown and Quiesce](../core/shutdown-and-quiesce.md)   
 [Recovery](../core/recovery.md)   
 [Application-Initiated Termination](../core/application-initiated-termination.md)   
 [LUSTATs\]](../core/lustats].md)   
 [Response Time Monitor Data](../core/response-time-monitor-data.md)