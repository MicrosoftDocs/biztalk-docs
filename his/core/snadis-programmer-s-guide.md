---
title: "SNADIS Programmer&#39;s Guide1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc707f56-483e-4de2-99e4-e90e0213738f
caps.latest.revision: 3
---
# SNADIS Programmer&#39;s Guide
This section enables original equipment manufacturers (OEMs) and adapter vendors who are developing their own SNALink software to work with [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] SNA Services.  
  
 SNALink software must be written as a Microsoft Windows device driver. For information about writing Windows device drivers, see the Windows Device Driver Kit (DDK).  
  
 This section provides the following information:  
  
-   Internal concepts of [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] that are required to integrate new communications adapters into the server environment.  
  
-   Definitions of the interfaces used by [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] to communicate with SNALinks.  
  
-   Information about using the configuration and diagnostics features included in [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)].  
  
-   Instructions for compiling and linking the SNALink support software.  
  
 The network operating systems currently supported by [!INCLUDE[hishostintegrationserver2009](../core/includes/hishostintegrationserver2009-md.md)] include Microsoft LAN Manager (as implemented in Microsoft Windows) and TCP/IP. Future versions of Host Integration Server may support other network operating systems. Because of this, it is recommended that you develop link support that is independent of the network operating system.  
  
 For API references and other technical materials for programming SNALink applications, see the [SNADIS Drivers Programmer's Reference](../Topic/SNADIS%20Drivers%20Programmer's%20Reference1.md) section of the SDK.  
  
 This section contains:  
  
-   [SNALink Concepts in Host Integration Server](../core/snalink-concepts-in-host-integration-server.md)  
  
-   [SNALink Interface](../core/snalink-interface.md)  
  
-   [SNALink Configuration Information](../core/snalink-configuration-information.md)  
  
-   [Data Link Control Interface](../core/data-link-control-interface.md)  
  
-   [Setup Information (SNADIS)](../core/setup-information-snadis.md)  
  
-   [Compiling and Linking a SNALink](../core/compiling-and-linking-a-snalink.md)  
  
-   [Synchronous Dumb Card Interface](../core/synchronous-dumb-card-interface.md)  
  
-   [SNA Modem Status Interface](../core/sna-modem-status-interface.md)  
  
-   [SNA Performance Monitor Interface](../core/sna-performance-monitor-interface.md)