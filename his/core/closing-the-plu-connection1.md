---
title: "Closing the PLU Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba0bf357-7632-4c38-9979-336de4c0c02a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Closing the PLU Connection
Either the application or the local node can terminate the primary logical unit (PLU) connection. The criteria for closing are:  
  
- The local node closes the PLU connection if it receives an **UNBIND** request from the host PLU, which terminates the PLU session. If the **UNBIND** type is **BIND forthcoming** (0x02), the local node sets the **BIND**-forthcoming indicator in the [Close(PLU) Request](./close-plu-request2.md), so that the application can reserve any necessary resources.  
  
- The local node closes the PLU connection if it receives a Deactivate Logical Unit (DACTLU) or Deactivate Physical Unit (DACTPU) request from the system services control point (SSCP).  
  
- The local node closes the PLU connection if it receives an outage notification from data link control.  
  
- The local node closes the PLU connection if it detects a critical error in a message from the application, putting the application in a critically failed state. In this case, the local node sends a **TERM-SELF** request to the host to elicit an **UNBIND**.  
  
- The application should close the PLU connection for logical power-off conditions. For example, if its resources are temporarily unavailable, or when the user finishes using the session.  
  
  When the local node issues a [Close(PLU) Request](./close-plu-request2.md), the application can determine the reason from the **Close** control field. There may be an associated status message on either the PLU connection (a [Status-Acknowledge(Nack-2)](./status-acknowledge-nack-2-2.md)) or the SSCP connection (a [Status-Session](./status-session2.md) message if the LU has been deactivated).  
  
  Whether the local node or the application closes the connection, the message is the same. The initiator of the **Close** sequence sends a **Close(PLU) Request** to its partner, which responds with a **Close(PLU) Response**. The **Close(PLU) Request** is unconditional. The **Close(PLU) Response** always reports that the connection was successfully closed.  
  
  The **Close(PLU) Response** is provided so that the initiator of the **Close** sequence can determine when outstanding data and status messages have been delivered. To avoid possible race conditions, the application should discard all messages it receives on the PLU connection after issuing a **Close(PLU) Request**, including any **Close(PLU) Request** messages from the local node, until it receives the **Close(PLU) Response**.  
  
  Note that, if the application sends a [Close(SSCP) Request](./close-sscp-request2.md) while the PLU session is active, the local node will close the PLU connection (as if **Close(PLU) Request** had been sent) as well as the SSCP connection.  
  
  The message sequence for an application-initiated **Close** is shown in the following figure. The local node sends a **TERM-SELF** request to the host to elicit an **UNBIND**.  
  
  If the host generates an **UNBIND** automatically on receipt of a **TERM-SELF**, the application can view **Close(PLU)** as equivalent to the termination of the PLU-SLU session.  
  
  ![](../core/media/his-32703h.gif "his_32703h")  
  Message sequence for an application-initiated Close  
  
  The message flow for a local node-initiated **Close** after receiving an **UNBIND** request from the host is shown in the following figure.  
  
  ![](../core/media/his-32703ha.gif "his_32703ha")  
  Message flow for a local node-initiated Close after receiving an UNBIND request  
  
  When an application is using the logical unit application (LUA) variant of the FMI, issuing a [Close(PLU) Request](./close-plu-request2.md) causes the node to immediately unbind the PLU session by sending an **UNBIND** request to the PLU. The **Close(PLU) Response** is returned to the application on receipt of the **UNBIND** response, as shown in the following figure.  
  
  ![](../core/media/his-32703hb.gif "his_32703hb")  
  Message flow for the Close(PLU) Response  
  
## See Also  
 [Opening the PLU Connection](../core/opening-the-plu-connection1.md)   
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
 [Response Time Monitor Data](../core/response-time-monitor-data1.md)