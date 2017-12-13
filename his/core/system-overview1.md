---
title: "System Overview1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa412efd-4c7a-42fe-bf8c-21648172266e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# System Overview
This topic outlines key points of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] implementation of the IP-DLC link service.  
  
-   The IP-DLC link service is configured and managed by the Host Integration Server administrator as for any other link service.  
  
-   To provide the support required for transporting dependent LU sessions across an APPN network, the IP-DLC link service runs the DLUR feature as defined by the SNA/APPN DLUR Architecture Reference. This provides dependent LU session support to a CS/390 host running the matching DLUS feature.  
  
-   The IP-DLC link service operates as a Branch Network Node (BrNN) as defined in the SNA/APPN Branch Extender Architecture Reference. When large numbers of Host Integration Server systems are connected to a mainframe, the Branch Network Node configuration ensures that the overhead of topology and network search traffic on the Host Integration Server and mainframe links is minimal—comparable to using Host Integration Server without the IP-DLC link service.  
  
-   Multiple IP-DLC link services can be configured, one for each local IP address on the Host Integration Server system.  
  
-   Multiple IP-DLC connections are supported for each IP-DLC link service. There is one IP-DLC connection for each PU local to Host Integration Server.  
  
-   Remote independent LUs are associated with an IP-DLC link service instead of a connection. All remote independent LUs accessible through an IP-DLC link service are associated with the single peer connection for the IP-DLC link service. All independent LU traffic is routed by the APPN network and may traverse any active HPR/IP link.  
  
## See Also  
 [Supported Features](../core/supported-features2.md)   
 [Scalability](../core/scalability1.md)   
 [Key Limitations](../core/key-limitations2.md)   
 [IP-DLC Link Service Concepts and Terminology](../core/ip-dlc-link-service-concepts-and-terminology1.md)