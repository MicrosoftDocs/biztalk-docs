---
title: "Opening a Connection (SNADIS)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65776df3-b005-493d-bc87-d53e30b1bf49
caps.latest.revision: 3
---
# Opening a Connection (SNADIS)
The 2.1 node is capable of supporting multiple connections through one or more SNALinks. For each connection, the node opens two Locality Partner Index (LPI) connections to the SNALink:  
  
-   LINK LPI connection to handle activation and deactivation of the connection.  
  
-   STATION LPI connection to transfer data to and from the remote station.  
  
 The one exception to this rule is the case of primary multipoint connections where there is a single LINK LPI connection and multiple STATION LPI connections. This special case is described in [SDLC Multipoint Connections](../core/sdlc-multipoint-connections.md).  
  
 The following messages flow over the data link control (DLC) interface and are used to activate a connection to a remote station.  
  
|Message|Description|  
|-------------|-----------------|  
|[Open(LINK) Request](../Topic/Open\(LINK\)%20Request2.md)|-   Flows from node to DLC over LINK connection.<br />-   Opens the LINK LPI connection between the node and the SNALink.<br />-   Provides configuration data for the SNALink.<br />-   Provides link connection data such as Token Ring address for the remote station.|  
|[Open(LINK) Response](../Topic/Open\(LINK\)%20Response1.md)|-   Flows from DLC to node over LINK connection.<br />-   Reports whether the SNALink has accepted the **Open(LINK) Request**.<br />-   Returns certain link-specific configuration parameters to the local node.<br />-   Can be an OK Response or an Error Response.|  
|[Request-Open-Station](../Topic/Request-Open-Station1.md)|-   Flows from DLC to node over LINK connection.<br />-   Passes an XID received from the SNALink up to the node.<br />-   Indicates that the SNALink has received a mode setting command, such as SNRM over SDLC, or SABME over 802.2.|  
|[Send-XID](../Topic/Send-XID2.md)|-   Flows from node to DLC over LINK connection.<br />-   Passes an XID from the node to the SNALink to be sent out over the link to the remote station.|  
|[Open(STATION) Request](../Topic/Open\(STATION\)%20Request1.md)|-   Flows from node to DLC over STATION connection.<br />-   Opens the STATION LPI connection between the node and the SNALink.<br />-   Specifies certain station-specific configuration information.|  
|[Open(STATION) OK Response](../Topic/Open\(STATION\)%20OResponse2.md)<br /><br /> –or–<br /><br /> [Open(STATION) Error Response](../Topic/Open\(STATION\)%20Error%20Response2.md)|-   Flows from DLC to node over STATION connection.<br />-   Acknowledges **Open(STATION) Request**.|  
|[Station-Contacted](../Topic/Station-Contacted2.md)|-   Flows from DLC to node over STATION connection.<br />-   Informs the local node that the link is now ready for data transfer.|  
  
 The use of these messages in activating various types of connections is described throughout the rest of this section. For information about the format of the messages, see [SNADIS Message Formats](../Topic/SNADIS%20Message%20Formats1.md).  
  
 The name of the Request-Open-Station message is historical. In earlier versions of the DLC interface, the higher-level software (such as the local node) always sent an **Open(STATION) Request** in response to this message—hence the name Request-Open-Station. However, now that multiple XIDs can be exchanged before the link is activated, the **Open(STATION) Request** is only sent at the end of the XID exchange.  
  
 The Request-Open-Station message now has two distinct semantic meanings:  
  
-   A Receive-XID  
  
-   A Receive-Set-Mode  
  
## In This Section  
  
-   [Opening the LINK LPI Connection](../core/opening-the-linlpi-connection.md)  
  
-   [Activating a Host Connection](../core/activating-a-host-connection-snadis.md)  
  
-   [Activating a Peer Connection](../core/activating-a-peer-connection-snadis.md)  
  
-   [Opening the STATION LPI Connection](../core/opening-the-station-lpi-connection.md)  
  
-   [Node Identification and Signaling Information](../core/node-identification-and-signaling-information.md)  
  
-   [XID Retries](../core/xid-retries.md)  
  
-   [Multiple Connections](../core/multiple-connections.md)