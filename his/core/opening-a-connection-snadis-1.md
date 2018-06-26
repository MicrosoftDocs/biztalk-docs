---
title: "Opening a Connection (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65776df3-b005-493d-bc87-d53e30b1bf49
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Opening a Connection (SNADIS)
The 2.1 node is capable of supporting multiple connections through one or more SNALinks. For each connection, the node opens two Locality Partner Index (LPI) connections to the SNALink:  
  
- LINK LPI connection to handle activation and deactivation of the connection.  
  
- STATION LPI connection to transfer data to and from the remote station.  
  
  The one exception to this rule is the case of primary multipoint connections where there is a single LINK LPI connection and multiple STATION LPI connections. This special case is described in [SDLC Multipoint Connections](../core/sdlc-multipoint-connections1.md).  
  
  The following messages flow over the data link control (DLC) interface and are used to activate a connection to a remote station.  
  
|Message|Description|  
|-------------|-----------------|  
|[Open(LINK) Request](./open-link-request1.md)|-   Flows from node to DLC over LINK connection.<br />-   Opens the LINK LPI connection between the node and the SNALink.<br />-   Provides configuration data for the SNALink.<br />-   Provides link connection data such as Token Ring address for the remote station.|  
|[Open(LINK) Response](./open-link-response2.md)|-   Flows from DLC to node over LINK connection.<br />-   Reports whether the SNALink has accepted the **Open(LINK) Request**.<br />-   Returns certain link-specific configuration parameters to the local node.<br />-   Can be an OK Response or an Error Response.|  
|[Request-Open-Station](./request-open-station2.md)|-   Flows from DLC to node over LINK connection.<br />-   Passes an XID received from the SNALink up to the node.<br />-   Indicates that the SNALink has received a mode setting command, such as SNRM over SDLC, or SABME over 802.2.|  
|[Send-XID](./send-xid1.md)|-   Flows from node to DLC over LINK connection.<br />-   Passes an XID from the node to the SNALink to be sent out over the link to the remote station.|  
|[Open(STATION) Request](./open-station-request2.md)|-   Flows from node to DLC over STATION connection.<br />-   Opens the STATION LPI connection between the node and the SNALink.<br />-   Specifies certain station-specific configuration information.|  
|[Open(STATION) OK Response](./open-station-oresponse1.md)<br /><br /> –or–<br /><br /> [Open(STATION) Error Response](./open-station-error-response1.md)|-   Flows from DLC to node over STATION connection.<br />-   Acknowledges **Open(STATION) Request**.|  
|[Station-Contacted](./station-contacted1.md)|-   Flows from DLC to node over STATION connection.<br />-   Informs the local node that the link is now ready for data transfer.|  
  
 The use of these messages in activating various types of connections is described throughout the rest of this section. For information about the format of the messages, see [SNADIS Message Formats](./snadis-message-formats2.md).  
  
 The name of the Request-Open-Station message is historical. In earlier versions of the DLC interface, the higher-level software (such as the local node) always sent an **Open(STATION) Request** in response to this message—hence the name Request-Open-Station. However, now that multiple XIDs can be exchanged before the link is activated, the **Open(STATION) Request** is only sent at the end of the XID exchange.  
  
 The Request-Open-Station message now has two distinct semantic meanings:  
  
-   A Receive-XID  
  
-   A Receive-Set-Mode  
  
## In This Section  
  
-   [Opening the LINK LPI Connection](../core/opening-the-linlpi-connection2.md)  
  
-   [Activating a Host Connection](../core/activating-a-host-connection-snadis-2.md)  
  
-   [Activating a Peer Connection](../core/activating-a-peer-connection-snadis-1.md)  
  
-   [Opening the STATION LPI Connection](../core/opening-the-station-lpi-connection2.md)  
  
-   [Node Identification and Signaling Information](../core/node-identification-and-signaling-information2.md)  
  
-   [XID Retries](../core/xid-retries2.md)  
  
-   [Multiple Connections](../core/multiple-connections1.md)