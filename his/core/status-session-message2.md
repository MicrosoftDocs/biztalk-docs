---
title: "Status-Session Message2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4278bf36-c9f6-4ff5-bd53-79d8d415e24b
caps.latest.revision: 3
---
# Status-Session Message
[Status-Session](../core/status-session1.md) messages always flow from the local node to the application and provide information about changes in the state of the session. There are separate **Status-Session** flows for each connection between the application and the local node.  
  
 The local node uses only one **Status-Session** message on the primary logical unit (PLU) connection. This is the **Status-Session(BETB)** message, used to report when the PLU session returns to the between-bracket state after the application or the PLU initiated a bracket. (For more information, see [Brackets](../core/brackets2.md).)  
  
 The local node reports the activation and deactivation states of the system services control point (SSCP) session and PU-SSCP session using **Status-Session** messages. For example, it reports the receipt of an **ACTLU** request from the host SSCP using a **Status-Session (LU-Active)** message on the SSCP connection. (For more information, see [SSCP Connection](../core/sscp-connection2.md).)  
  
 By providing **Status-Session** messages rather than requiring the application to interpret the relevant information in the SNA request, the local node shields the application from decisions affecting conditional state transitions and from the necessity for a detailed understanding of SNA protocols.  
  
 A **Status-Session** message contains a status code, and for some status codes, an additional status code that qualifies the meaning of the primary status code. For example, the Link-Error status code, which occurs on the SSCP connection, is qualified by a status code that reports the link outage code supplied by the data link control layer of the local node. Applications such as 3270 device emulators use the qualifying status codes to display communications check codes ( –+z_nnn ) on the status line of the display.  
  
 The **Status-Session** codes are summarized in [Status-Session Codes](../core/status-session-codes2.md).  
  
## See Also  
 [Status-Acknowledge Message](../core/status-acknowledge-message2.md)   
 [Status-Control Message](../core/status-control-message2.md)   
 [Status-Error Message](../core/status-error-message2.md)   
 [Status-Resource Message](../core/status-resource-message2.md)   
 [Status-RTM Message](../core/status-rtm-message2.md)