---
title: "Closing the SSCP Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d4b87d5-e0ec-45a7-a38b-47147e2310a0
caps.latest.revision: 3
---
# Closing the SSCP Connection
To close the system services control point (SSCP) connection, an application sends a [Close(SSCP) Request](../core/close-sscp-request1.md) to the local node, which responds with a [Close(SSCP) Response](../core/close-sscp-response2.md). The **Close(SSCP) Request** is unconditional. The **Close(SSCP) Response** always reports that the connection was successfully closed. The **Close(SSCP) Response** is provided so that applications can determine when outstanding data and status messages on the session have been delivered.  
  
 If the logical unit (LU) is bound, the local node sends a **TERM-SELF** message to the SSCP on behalf of the application to elicit an **UNBIND**. An application that needs to be unbound can issue **Close(PLU)**. (For more information, see [Closing the PLU Connection](../core/closing-the-plu-connection2.md).) Normally, the SSCP connection can be maintained while the application task is active, even if it is idle.  
  
 Closing the connection invalidates the locality, partner, index (LPI) pair for the connection, but does not alter the state of the SSCP session. The following figure shows the message flow.  
  
 ![](../core/media/his-32703e.gif "his_32703e")  
Message flow for closing a connection  
  
## See Also  
 [Opening the SSCP Connection](../core/opening-the-sscp-connection2.md)   
 [SSCP Session](../core/sscp-session1.md)   
 [RTM Parameters\]](../core/rtm-parameters]1.md)   
 [3270 User Alerts](../core/3270-user-alerts1.md)