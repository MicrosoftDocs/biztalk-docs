---
title: "3270 User Alerts | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 091c1909-3f9c-4b68-b9e5-5058eb0a4797
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# 3270 User Alerts
The Host Integration Server 3270 emulation program can send 3270 user alerts to the local node on the system services control point (SSCP) connection. This enables the local node to route each alert to the appropriate host for the 3270 session on which it was sent.  
  
 To send a 3270 user alert, the application should send it as a [Data](data1.md) message on the SSCP connection. The local node will recognize it as a 3270 user alert if both of the following are true:  
  
- The function management header indicator (FMHI) bit in the application flag is set.  
  
- The first three bytes of the data are 0x41038D, indicating a Network Management Vector Transport (NMVT).  
  
  The local node sends the alert to the appropriate host for the 3270 session on which it was received. If a relative time subvector is present (0x42) with increment type 0xEF (sequence), the local node sets the sequence number in each message (starting at one from power-up and incrementing by one for each message sent). Host Integration Server allows sequence number values up to 2^16. Apart from this, the local node does not alter the contents of the alert.  
  
> [!NOTE]
>  There can be some delay before the application receives a response to the alert. The response is sent on the SSCP connection in the same way as other data on this connection. The application must not send further data on the SSCP connection (including further alerts) until it has received a response to this alert.  
  
## See Also  
 [Opening the SSCP Connection](../core/opening-the-sscp-connection1.md)   
 [Closing the SSCP Connection](../core/closing-the-sscp-connection2.md)   
 [SSCP Session](../core/sscp-session2.md)   
 [RTM Parameters\]](../core/rtm-parameters]2.md)