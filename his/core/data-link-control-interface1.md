---
title: "Data Link Control Interface1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e573c41e-b75e-4d92-854b-11fa26f2a8e7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Link Control Interface
The data link control (DLC) interface defines the interface between the local 2.1 node and an SNALink. The DLC interface is defined in terms of the messages that are sent across the interface. Note that this is logically distinct from the definition of the Base/Dynamic Access Module (DMOD) interface, which defines the API used to send messages between two components in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] (for example, between the local node and an SNALink).  
  
 DLC messages are exchanged between the local node and an SNALink across LPI connections. For details, see [Structure of SNALink Components](../core/structure-of-snalink-components1.md).  
  
 The local node uses the DLC interface to:  
  
-   Activate DLC connections.  
  
-   Exchange format 0 or format 3 XIDs for station activation.  
  
-   Exchange DLC information frames.  
  
-   Handle DLC error notification.  
  
## In This Section  
  
-   [Supported Configurations (SNADIS)](../core/supported-configurations-snadis-2.md)  
  
-   [Opening a Connection (SNADIS)](../core/opening-a-connection-snadis-1.md)  
  
-   [DLC Information Transfer](../core/dlc-information-transfer2.md)  
  
-   [Closing a Connection (SNADIS)](../core/closing-a-connection-snadis-1.md)  
  
-   [Incoming Call Support (SNADIS)](../core/incoming-call-support-snadis-2.md)  
  
-   [SDLC Multipoint Connections](../core/sdlc-multipoint-connections1.md)