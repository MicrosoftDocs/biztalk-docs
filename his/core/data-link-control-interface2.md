---
title: "Data Link Control Interface2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c1db607-d680-4d0f-a8bf-d5ba9be2e2c5
caps.latest.revision: 3
---
# Data Link Control Interface
The data link control (DLC) interface defines the interface between the local 2.1 node and an SNALink. The DLC interface is defined in terms of the messages that are sent across the interface. Note that this is logically distinct from the definition of the Base/Dynamic Access Module (DMOD) interface, which defines the API used to send messages between two components in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] (for example, between the local node and an SNALink).  
  
 DLC messages are exchanged between the local node and an SNALink across LPI connections. For details, see [Structure of SNALink Components](../core/structure-of-snalink-components2.md).  
  
 The local node uses the DLC interface to:  
  
-   Activate DLC connections.  
  
-   Exchange format 0 or format 3 XIDs for station activation.  
  
-   Exchange DLC information frames.  
  
-   Handle DLC error notification.  
  
## In This Section  
  
-   [Supported Configurations (SNADIS)](../core/supported-configurations-snadis-1.md)  
  
-   [Opening a Connection (SNADIS)](../core/opening-a-connection-snadis-2.md)  
  
-   [DLC Information Transfer](../core/dlc-information-transfer1.md)  
  
-   [Closing a Connection (SNADIS)](../core/closing-a-connection-snadis-2.md)  
  
-   [Incoming Call Support (SNADIS)](../core/incoming-call-support-snadis-1.md)  
  
-   [SDLC Multipoint Connections](../core/sdlc-multipoint-connections2.md)