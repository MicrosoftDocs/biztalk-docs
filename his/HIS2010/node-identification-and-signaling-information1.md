---
title: "Node Identification and Signaling Information1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c08ef6f0-7383-41cb-973d-0af3c3ae84b4
caps.latest.revision: 3
---
# Node Identification and Signaling Information
For information about the role an SNALink plays in node identification, see [Incoming Call Support](../HIS2010/incoming-call-support-snadis-1.md).  
  
 When exchange identifications (XIDs) are exchanged, there are two mechanisms for identifying the remote station:  
  
-   The node identifier on received XIDs.  
  
-   The data link control (DLC) defined address; for example, the media access control (MAC) address. This is known as signaling information.  
  
 The presence of signaling information depends on the type of the SNALink. For instance, there is no signaling information over a Synchronous Data Link Control (SDLC) link, but there is signaling information over X.25 and 802.2. The SNALink passes signaling information to the local node on the [Request-Open-Station](../HIS2010/request-open-station1.md) message by appending it after the XID.  
  
 If signaling information is present, the local node checks it against the configured value in the dial-digits record of the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] configuration file. For incoming call support, this allows the local node to determine the connection that is to be activated. For a fuller description of incoming calls, see [Incoming Call Support](../HIS2010/incoming-call-support-snadis-1.md).  
  
 If there is no signaling information, the local node compares the control point (CP) name on the received XID with the remote control point name in the configuration.  
  
 If the remote station is identified correctly, XID exchange proceeds as detailed in [Activating a Peer Connection](../HIS2010/activating-a-peer-connection-snadis-2.md). However, if there is a mismatch, the local node sends an XID (in the [Send-XID](../HIS2010/send-xid2.md) message) containing an error vector followed by a [Close(LINK) Request](../HIS2010/close-link-request2.md), as shown in the following figure.  
  
 ![](../core/media/dev3f.gif "dev3f")  
Local node sending an XID containing an error vector, followed by a Close(LINK) Request