---
title: "Opening the STATION LPI Connection2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d5d1cf2-ed13-43f4-86b2-9e7c5d7b38f4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Opening the STATION LPI Connection
After receiving a [Request-Open-Station](./request-open-station2.md) (RQOS) message, the local node sends an [Open(STATION)](./open-station-1.md) message to the SNALink when:  
  
- The station is configured as secondary (or has negotiated to secondary), and the RQOS message has the Rcv-Set-Mode flag on, indicating that the SNALink has received a mode-setting command such as set normal response mode (SNRM).  
  
- The station is configured as primary (or has negotiated to primary), the RQOS message contains a secondary exchange identification (XID), and the local station has sent at least one negotiation-proceeding XID.  
  
  The [Open(STATION) Request](./open-station-request2.md) contains the link index that was on the [Open(LINK) Request](./open-link-request1.md). This field is used to correlate the LINK and STATION LPI connections for SNALinks that support multiple connections, such as X.25, 802.2, and channel.  
  
  This **Open(STATION) Request** contains configuration data for the link station, such as the Synchronous Data Link Control (SDLC) address of the adjacent link station (0x00 for secondary stations, 0x01 to 0xFE for primary stations).  
  
  The SNALink should use this address field for determining the local station's role. If it is set to 0x00, the local station is a secondary station. Otherwise, the local station is the primary station. This field has this meaning even when the address is not used because of the link type (such as 802.2).  
  
  See [Open(STATION) Request](./open-station-request2.md) for the format of this message.  
  
  If the station cannot be initialized (perhaps due to a lack of resources), the SNALink responds with an [Open(STATION) Error Response](./open-station-error-response1.md) containing the appropriate error code.