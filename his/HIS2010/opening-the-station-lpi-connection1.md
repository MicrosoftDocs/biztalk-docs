---
title: "Opening the STATION LPI Connection1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fb47d79-a5ff-4519-9bdf-fcb6a79a9bc8
caps.latest.revision: 3
---
# Opening the STATION LPI Connection
After receiving a [Request-Open-Station](../HIS2010/request-open-station1.md) (RQOS) message, the local node sends an [Open(STATION)](../HIS2010/open-station-2.md) message to the SNALink when:  
  
-   The station is configured as secondary (or has negotiated to secondary), and the RQOS message has the Rcv-Set-Mode flag on, indicating that the SNALink has received a mode-setting command such as set normal response mode (SNRM).  
  
-   The station is configured as primary (or has negotiated to primary), the RQOS message contains a secondary exchange identification (XID), and the local station has sent at least one negotiation-proceeding XID.  
  
 The [Open(STATION) Request](../HIS2010/open-station-request1.md) contains the link index that was on the [Open(LINK) Request](../HIS2010/open-link-request2.md). This field is used to correlate the LINK and STATION LPI connections for SNALinks that support multiple connections, such as X.25, 802.2, and channel.  
  
 This **Open(STATION) Request** contains configuration data for the link station, such as the Synchronous Data Link Control (SDLC) address of the adjacent link station (0x00 for secondary stations, 0x01 to 0xFE for primary stations).  
  
 The SNALink should use this address field for determining the local station's role. If it is set to 0x00, the local station is a secondary station. Otherwise, the local station is the primary station. This field has this meaning even when the address is not used because of the link type (such as 802.2).  
  
 See [Open(STATION) Request](../HIS2010/open-station-request1.md) for the format of this message.  
  
 If the station cannot be initialized (perhaps due to a lack of resources), the SNALink responds with an [Open(STATION) Error Response](../HIS2010/open-station-error-response2.md) containing the appropriate error code.