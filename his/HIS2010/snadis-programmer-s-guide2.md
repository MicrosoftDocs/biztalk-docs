---
title: "SNADIS Programmer&#39;s Guide2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84f13193-eb1b-4504-989f-4455493f7c90
caps.latest.revision: 4
---
# SNADIS Programmer&#39;s Guide
This section enables original equipment manufacturers (OEMs) and adapter vendors who are developing their own SNALink software to work with [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] SNA Services.  
  
 SNALink software must be written as a Microsoft Windows device driver. For information about writing Windows device drivers, see the Windows Device Driver Kit (DDK).  
  
 This section provides the following information:  
  
-   Internal concepts of [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] that are required to integrate new communications adapters into the server environment.  
  
-   Definitions of the interfaces used by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] to communicate with SNALinks.  
  
-   Information about using the configuration and diagnostics features included in [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
-   Instructions for compiling and linking the SNALink support software.  
  
 The network operating systems currently supported by [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] include Microsoft LAN Manager (as implemented in Microsoft Windows) and TCP/IP. Future versions of Host Integration Server may support other network operating systems. Because of this, it is recommended that you develop link support that is independent of the network operating system.  
  
 For API references and other technical materials for programming SNALink applications, see the [SNADIS Drivers Programmer's Reference](../HIS2010/snadis-drivers-programmer-s-reference1.md) section of the SDK.  
  
 This section contains:  
  
-   [SNALink Concepts in Host Integration Server](../HIS2010/snalink-concepts-in-host-integration-server2.md)  
  
-   [SNALink Interface](../HIS2010/snalink-interface2.md)  
  
-   [SNALink Configuration Information](../HIS2010/snalink-configuration-information2.md)  
  
-   [Data Link Control Interface](../HIS2010/data-link-control-interface2.md)  
  
-   [Setup Information (SNADIS)](../HIS2010/setup-information-snadis-2.md)  
  
-   [Compiling and Linking a SNALink](../HIS2010/compiling-and-linking-a-snalink1.md)  
  
-   [Synchronous Dumb Card Interface](../HIS2010/synchronous-dumb-card-interface2.md)  
  
-   [SNA Modem Status Interface](../HIS2010/sna-modem-status-interface2.md)  
  
-   [SNA Performance Monitor Interface](../HIS2010/sna-performance-monitor-interface2.md)